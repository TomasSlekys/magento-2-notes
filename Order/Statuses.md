# Add custom order statuses

`CreationLabs/SmartDeal/Setup/Patch/Data/AddOrderStatuses.php`
```php
<?php

declare(strict_types=1);

namespace CreationLabs\SmartDeal\Setup\Patch\Data;

use CreationLabs\SmartDeal\Api\OrderInterface;
use Exception;
use Magento\Framework\Exception\LocalizedException;
use Magento\Framework\Setup\Patch\DataPatchInterface;
use Magento\Sales\Model\Order;
use Magento\Sales\Model\Order\StatusFactory;
use Magento\Sales\Model\ResourceModel\Order\StatusFactory as StatusResourceFactory;

class AddOrderStatuses implements DataPatchInterface
{
    protected StatusFactory $statusFactory;

    protected StatusResourceFactory $statusResourceFactory;

    public function __construct(
        StatusFactory $statusFactory,
        StatusResourceFactory $statusResourceFactory
    ) {
        $this->statusFactory = $statusFactory;
        $this->statusResourceFactory = $statusResourceFactory;
    }

    /**
     * @return $this
     * @throws LocalizedException
     * @throws Exception
     * @author CreationLabs
     */
    public function apply(): self
    {
        $statusData = [
            OrderInterface::MAGENTO_STATUS_PENDING => [
                'label' => (string) __('Klientas pradėjo sudarinėti sutartį'),
                'state' => Order::STATE_PENDING_PAYMENT
            ],
            OrderInterface::MAGENTO_STATUS_SIGNED => [
                'label' => (string) __('Klientas pasirašė sutartį'),
                'state' => Order::STATE_PROCESSING
            ],
            OrderInterface::MAGENTO_STATUS_DELIVERED => [
                'label' => (string) __('Klientui prekės pristatytos'),
                'state' => Order::STATE_COMPLETE
            ],
            OrderInterface::MAGENTO_STATUS_DECLINED => [
                'label' => (string) __('Finansavimas nesuteiktas'),
                'state' => Order::STATE_CANCELED
            ],
            OrderInterface::MAGENTO_STATUS_ANNULLED => [
                'label' => (string) __('Klientas atšaukė sutarties sudarymą / sutartį'),
                'state' => Order::STATE_CANCELED
            ],
            OrderInterface::MAGENTO_STATUS_REFUNDED => [
                'label' => (string) __('Sutartis nutraukta / atšaukta'),
                'state' => Order::STATE_CANCELED
            ],
        ];

        foreach ($statusData as $statusCode => $statusDatum) {
            $status = $this->statusFactory->create();

            $status->setData(
                [
                    'status' => $statusCode,
                    'label' => $statusDatum['label'],
                ]
            );

            $statusResource = $this->statusResourceFactory->create();
            $statusResource->save($status);

            $status->assignState($statusDatum['state'], false, true);
        }

        return $this;
    }

    /**
     * @inheritdoc
     */
    public static function getDependencies(): array
    {
        return [];
    }

    /**
     * @inheritdoc
     */
    public function getAliases(): array
    {
        return [];
    }
}
```
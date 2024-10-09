# Deprecated use of Registry

## What to use instead

Use sessions instead:

Magento Customer Session – `\Magento\Customer\Model\Session`

Magento Checkout Session – `\Magento\Checkout\Model\Session`

Magento Catalog Session – `\Magento\Catalog\Model\Session`

Newsletter Session – `\Magento\Newsletter\Model\Session`

## Example

### Before

```php
public function __construct(
    private readonly \Magento\Framework\Registry $registry,
) {
}

public function getProduct(): \Magento\Catalog\Api\Data\ProductInterface
{
    return $this->registry->registry('product');
}
```

### After

```php
public function __construct(
    private readonly \Magento\Catalog\Model\Session $catalogSession,
    private readonly \Magento\Catalog\Api\ProductRepositoryInterface $productRepository
) {
}

public function getProduct(): ?\Magento\Catalog\Api\Data\ProductInterface
{
    if ($productId = $this->catalogSession->getData('last_viewed_product_id')) {
        try {
            return $this->productRepository->getById($productId);
        } catch (\Magento\Framework\Exception\NoSuchEntityException $e) {
            return null;
        }
    }
    
    return null;
}
```
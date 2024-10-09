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
    $product = $this->registry->registry('product');
}
```

### After

```php
public function __construct(
    private readonly \Magento\Catalog\Model\Session $catalogSession,
    private readonly \Magento\Catalog\Api\ProductRepositoryInterface $productRepository
) {
    $productId = $this->catalogSession->getData('last_viewed_product_id');
    $product = $this->productRepository->getById($productId);
}
```
# Repositories

## Get all categories

```php

use Magento\Framework\Api\SearchCriteriaBuilder;
use Magento\Catalog\Api\CategoryListInterface;

...

public function getCategoryCollection(): array
{
    $searchCriteria = $this->_searchCriteriaBuilder->create();

    return $this->_categoryListInterface->getList($searchCriteria)->getItems();
}
```
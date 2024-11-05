# Repositories

## Get all categories (With filters and sort order)

```php

use Magento\Framework\Api\SearchCriteriaBuilder;
use Magento\Catalog\Api\CategoryListInterface;
use Magento\Framework\Api\SearchCriteriaBuilder;
use Magento\Catalog\Api\CategoryListInterface;
use Magento\Framework\Api\SortOrder;
use Magento\Framework\Api\SortOrderBuilderFactory;

/**
 * @var SearchCriteriaBuilder
 */
private $_searchCriteriaBuilder;

/**
 * @var CategoryListInterface
 */
private $_categoryListInterface;

/**
 * @var SortOrderBuilderFactory
 */
private $_sortOrderBuilderFactory;

public function __construct(
    SearchCriteriaBuilder $searchCriteriaBuilder,
    CategoryListInterface $categoryListInterface,
    SortOrderBuilderFactory $sortOrderBuilderFactory
) {
    $this->_searchCriteriaBuilder = $searchCriteriaBuilder;
    $this->_categoryListInterface = $categoryListInterface;
    $this->_sortOrderBuilderFactory = $sortOrderBuilderFactory;
}

public function getCategoryCollection(): array
{
    $searchCriteria = $this->_searchCriteriaBuilder->create();
    
    $this->_searchCriteriaBuilder->addFilter('entity_id', $childrenCategoryIds, 'in');
    $this->_searchCriteriaBuilder->addFilter(CategoryInterface::KEY_IS_ACTIVE, 1);

    $this->_searchCriteriaBuilder->addSortOrder(
        $sortOrderBuilder->setField('position')->setDirection(SortOrder::SORT_ASC)->create()
    );

    $searchCriteria = $this->_searchCriteriaBuilder->create();

    return $this->_categoryListInterface->getList($searchCriteria)->getItems();
}
```
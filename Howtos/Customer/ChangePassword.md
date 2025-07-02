# Change customer password via DB query

1. Create a temporary file `genpass.php` with the following content in the root of your Magento installation (change the password as needed):

```php
require __DIR__ . '/app/bootstrap.php';

use Magento\Framework\App\Bootstrap;
use Magento\Framework\App\ObjectManager;

$params = $_SERVER;
$bootstrap = Bootstrap::create(BP, $params);
$obj = $bootstrap->getObjectManager();

$state = $obj->get(\Magento\Framework\App\State::class);
$state->setAreaCode('frontend');

$password = '1gM386+yW)TS'; // change this
$encryptor = $obj->get(\Magento\Framework\Encryption\EncryptorInterface::class);
$hash = $encryptor->getHash($password, true);

echo "Hashed password: " . $hash . PHP_EOL;
```

2. Run the script from the command line:

```bash
php genpass.php
````

3. Copy the output hash.
4. Open your database and run the following SQL query to update the customer's password (ensure to replace the email with the customer's email and the hash with the one you copied):

```sql
UPDATE customer_entity
SET password_hash = '80d99e0cb334073244a164f287c3c59feece69235f1c56549bef80298aa9acf1:nWyc8i6yUCw98AxRB3Kw1HW7gLA1qeCD:3_32_2_67108864'
WHERE email = 'some.email@example.com';
```

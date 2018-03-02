# Jerry Memo CRUD with PHP PDO MySQL
 
## Connection 連線

$host = '127.0.0.1';

$dbname = '';

$username = 'root';
$password = '';
$charset = 'utf8';
$collate = 'utf8_unicode_ci';
$dsn = "mysql:host=$host;dbname=$dbname;charset=$charset";
$options = [
    PDO::MYSQL_ATTR_INIT_COMMAND => "SET NAMES $charset COLLATE $collate"
];

## Select one row 查詢單筆

$pdo = new PDO($dsn, $username, $password, $options);
$obj = $pdo->prepare("Your SQL");
$obj->execute();

//PDO::FETCH_OBJ for Strong Type or PDO::FETCH_ASSOC for Array
while ($row = $obj->fetch(PDO::FETCH_OBJ)) {
    echo $row->your_property.'<br/>';
}


## Select Where 查詢條件
$id = 1;
$obj = $pdo->prepare("SELECT ... WHERE dmId = :id ");
$obj->bindParam(':id',$id,PDO::PARAM_INT); //PARAM_INT or 【PDO::PARAM_STR, length】
$obj->execute();

while ($row = $obj->fetch(PDO::FETCH_OBJ)) {
    echo $row->your_property.'<br/>';
}

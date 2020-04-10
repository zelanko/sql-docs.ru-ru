---
title: PDOStatement::getColumnMeta | Документация Майкрософт
ms.custom: ''
ms.date: 01/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c92a21cc-8e53-43d0-a4bf-542c77c100c9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fafc4b7bfcd72db1898e0a76b2ff43b3638f1f49
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925301"
---
# <a name="pdostatementgetcolumnmeta"></a>PDOStatement::getColumnMeta
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Извлекает метаданные для столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array PDOStatement::getColumnMeta ( $column );  
```  
  
#### <a name="parameters"></a>Параметры  
*$conn*: отсчитываемый от нуля номер столбца (целое число), метаданные которого требуется извлечь.  
  
## <a name="return-value"></a>Возвращаемое значение  
Ассоциативный массив (ключ и значение), содержащий метаданные для столбца. Описание полей в массиве см. в разделе "Примечания".  
  
## <a name="remarks"></a>Remarks  
В следующей таблице перечислены поля в массиве, возвращенном getColumnMeta.  
  
|NAME|VALUES|  
|--------|----------|  
|native_type|Указывает тип PHP для столбца. Всегда строка.|  
|driver:decl_type|Указывает тип SQL, используемый для представления значения столбца в базе данных. Если столбец в результирующем наборе является результатом функции, это значение не возвращается PDOStatement::getColumnMeta.|  
|flags|Указывает флаги, установленные для этого столбца. Всегда равно 0.|  
|name|Указывает имя столбца в базе данных.|  
|table|Указывает имя таблицы, содержащей столбец в базе данных. Всегда пусто.|  
|len|Указывает длину столбца.|  
|precision|Указывает числовую точность этого столбца.|  
|pdo_type|Указывает тип этого столбца, представленный константами PDO::PARAM_*. Всегда PDO::PARAM_STR (2).|  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$stmt = $conn->query("select * from Person.ContactType");  
$metadata = $stmt->getColumnMeta(2);  
var_dump($metadata);  
  
print $metadata['sqlsrv:decl_type'] . "\n";  
print $metadata['native_type'] . "\n";  
print $metadata['name'];  
?>  
```  
  
## <a name="sensitivity-data-classification-metadata"></a>Метаданные классификации данных о конфиденциальности

Начиная с версии 5.8.0, пользователям доступен новый атрибут инструкции `PDO::SQLSRV_ATTR_DATA_CLASSIFICATION`, который позволяет получать [метаданные классификации данных о конфиденциальности](https://docs.microsoft.com/sql/relational-databases/security/sql-data-discovery-and-classification?view=sql-server-ver15&tabs=t-sql#subheading-4) из Microsoft SQL Server 2019 с помощью `PDOStatement::getColumnMeta`. Для этого требуется драйвер Microsoft ODBC Driver версии 17.4.2 или выше.

Обратите внимание, что атрибут `PDO::SQLSRV_ATTR_DATA_CLASSIFICATION` по умолчанию имеет значение `false`, но вы можете указать значение `true`, и тогда массив упомянутого выше поля `flags` будет заполнен метаданными классификации данных о конфиденциальности, если они существуют. 

В качестве примера рассмотрим таблицу Patients:

```
CREATE TABLE Patients 
      [PatientId] int identity,
      [SSN] char(11),
      [FirstName] nvarchar(50),
      [LastName] nvarchar(50),
      [BirthDate] date)
```

Столбцы SSN и BirthDate можно классифицировать следующим образом:

```
ADD SENSITIVITY CLASSIFICATION TO [Patients].SSN WITH (LABEL = 'Highly Confidential - secure privacy', INFORMATION_TYPE = 'Credentials')
ADD SENSITIVITY CLASSIFICATION TO [Patients].BirthDate WITH (LABEL = 'Confidential Personal Data', INFORMATION_TYPE = 'Birthdays')
```

Чтобы получить доступ к метаданным, установите для `PDOStatement::getColumnMeta` значение true и примените `PDO::SQLSRV_ATTR_DATA_CLASSIFICATION`, как показано в следующем фрагменте кода:

```
$options = array(PDO::SQLSRV_ATTR_DATA_CLASSIFICATION => true);
$tableName = 'Patients';
$tsql = "SELECT * FROM $tableName";
$stmt = $conn->prepare($tsql, $options);
$stmt->execute();
$numCol = $stmt->columnCount();

for ($i = 0; $i < $numCol; $i++) {
    $metadata = $stmt->getColumnMeta($i);
    $jstr = json_encode($metadata);
    echo $jstr . PHP_EOL;
}
```

Выходные данные содержат метаданные для всех столбцов:

```
{"flags":{"Data Classification":[]},"sqlsrv:decl_type":"int identity","native_type":"string","table":"","pdo_type":2,"name":"PatientId","len":10,"precision":0}
{"flags":{"Data Classification":[{"Label":{"name":"Highly Confidential - secure privacy","id":""},"Information Type":{"name":"Credentials","id":""}}]},"sqlsrv:decl_type":"char","native_type":"string","table":"","pdo_type":2,"name":"SSN","len":11,"precision":0}
{"flags":{"Data Classification":[]},"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"FirstName","len":50,"precision":0}
{"flags":{"Data Classification":[]},"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"LastName","len":50,"precision":0}
{"flags":{"Data Classification":[{"Label":{"name":"Confidential Personal Data","id":""},"Information Type":{"name":"Birthdays","id":""}}]},"sqlsrv:decl_type":"date","native_type":"string","table":"","pdo_type":2,"name":"BirthDate","len":10,"precision":0}
```

Если мы изменим приведенный выше фрагмент кода так, чтобы параметр `PDO::SQLSRV_ATTR_DATA_CLASSIFICATION` имел значение `false` (вариант по умолчанию), поле `flags` снова будет получать значение `0`, как показано ниже:

```
{"flags":0,"sqlsrv:decl_type":"int identity","native_type":"string","table":"","pdo_type":2,"name":"PatientId","len":10,"precision":0}
{"flags":0,"sqlsrv:decl_type":"char","native_type":"string","table":"","pdo_type":2,"name":"SSN","len":11,"precision":0}
{"flags":0,"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"FirstName","len":50,"precision":0}
{"flags":0,"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"LastName","len":50,"precision":0}
{"flags":0,"sqlsrv:decl_type":"date","native_type":"string","table":"","pdo_type":2,"name":"BirthDate","len":10,"precision":0}
```

      
## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

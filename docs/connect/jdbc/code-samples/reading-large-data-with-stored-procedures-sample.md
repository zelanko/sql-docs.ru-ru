---
title: Пример считывания большого объема данных с помощью хранимых процедур | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 58c76635-a117-4661-8781-d6cb231c5809
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 924bcf388ddf74f3be3f4bb13f83e00789fb8777
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "69028298"
---
# <a name="reading-large-data-with-stored-procedures-sample"></a>Пример считывания большого объема данных с помощью хранимых процедур

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

В этом примере приложения, использующего драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], показано получение большого параметра OUT из хранимой процедуры.

Файл кода для этого образца имеет имя ExecuteStoredProcedure.java и находится в следующей папке:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>Требования

Для запуска этого образца приложения также потребуется доступ к образцу базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Кроме того, включите в параметр classpath путь к файлу mssql-jdbc.jar. Дополнительные сведения о том, как настроить параметр classpath, см. в статье [Использование JDBC Driver](../../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] включает файлы библиотек классов mssql-jdbc, которые используются в зависимости от выбранных параметров среды выполнения Java (JRE). Дополнительные сведения о выборе JAR-файла см. в описании [требований к системе для JDBC Driver](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

Создайте следующую хранимую процедуру в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]:

```sql
CREATE PROCEDURE GetLargeDataValue
  (@Document_ID int,
   @Document_ID_out int OUTPUT,
   @Document_Title varchar(50) OUTPUT,  
   @Document_Summary nvarchar(max) OUTPUT)  

AS
BEGIN
   SELECT @Document_ID_out = DocumentID,
          @Document_Title = Title,  
          @Document_Summary = DocumentSummary
    FROM  Production.Document  
    WHERE DocumentID = @Document_ID  
END  
```

## <a name="example"></a>Пример

В следующем примере образец кода будет использоваться для соединения с базой данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Затем образец кода создает образцы данных и обновляет таблицу Production.Document с помощью параметризированного запроса. Затем в образце кода включается режим адаптивной буферизации с помощью метода [getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) класса [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) и выполняется хранимая процедура GetLargeDataValue. Обратите внимание, что, начиная с версии драйвера JDBC 2.0, свойство соединения responseBuffering по умолчанию имеет значение «adaptive».

Наконец, в образце кода выводятся возвращенные данные с параметрами OUT и демонстрируется использование методов `mark` и `reset` в потоке для повторного считывания любого фрагмента данных.

[!code[JDBC#UsingAdaptiveBuffering2](../../../connect/jdbc/codesnippet/Java/reading-large-data-with-_1_1.java)]

## <a name="see-also"></a>См. также раздел

[Работа с большими объемами данных](../../../connect/jdbc/code-samples/working-with-large-data.md)

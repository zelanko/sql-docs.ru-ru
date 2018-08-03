---
title: Пример считывания данных большого объема с помощью хранимых процедур | Документы Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 58c76635-a117-4661-8781-d6cb231c5809
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fcbeba3d535450001c15ab3168df9da59f7dceb2
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279036"
---
# <a name="reading-large-data-with-stored-procedures-sample"></a>Образец считывания данных большого объема с помощью хранимых процедур
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В этом примере приложения, использующего драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], показано получение большого параметра OUT из хранимой процедуры.  
  
 Файл кода для этого образца имеет имя ExecuteStoredProcedure.java и находится в следующей папке:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \samples\adaptive  
  
## <a name="requirements"></a>Требования  
 Для запуска этого образца приложения также потребуется доступ к образцу базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Также можно задайте параметр Classpath путь к JAR-файл mssql-jdbc. Дополнительные сведения о том, как путь к классу см. в разделе [с помощью драйвера JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] включает файлы библиотек классов mssql-jdbc, которые используются в зависимости от выбранных параметров среды выполнения Java (JRE). Дополнительные сведения о какие файлы JAR следует выбрать, см. в разделе [требования к системе для драйвера JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [Работа с большими объемами данных](../../../connect/jdbc/working-with-large-data.md)  
  
  

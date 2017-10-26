---
title: "Чтение больших объемов данных образец | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c986144-3854-4352-8331-e79eccbefc28
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4341d85ceced60ed2d108eb4e9f95251e6fdd33d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="reading-large-data-sample"></a>Образец считывания данных большого объема
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Это [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] образец приложения показано, как получить большое значение одного столбца из [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с помощью [getCharacterStream](../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md) метод.  
  
 Файл кода для этого образца имеет имя readLargeData.java и находится в следующей папке:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \samples\adaptive  
  
## <a name="requirements"></a>Требования  
 Чтобы запустить этот образец приложения, потребуется доступ к [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных. Необходимо также включить в путь к классу файл sqljdbc.jar или sqljdbc4.jar. Если в пути к классу не указан файл sqljdbc.jar или sqljdbc4.jar, то образец приложения вызовет распространенное исключение «Класс не найден». Дополнительные сведения о том, как задать значение переменной classpath см. в разделе [с помощью драйвера JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Предоставляет файлы библиотек классов для использования в зависимости от выбранных параметров среды выполнения Java (JRE) sqljdbc.jar и sqljdbc4.jar. Дополнительные сведения о какие файлы JAR следует выбрать см. в разделе [требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Пример  
 В следующем примере образец кода устанавливает соединение для [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] базы данных. Затем образец кода создает образцы данных и обновляет таблицу Production.Document с помощью параметризированного запроса.  
  
 Кроме того, в образце кода показано, как получить режим адаптивной буферизации с помощью [getResponseBuffering](../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) метод [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класса. Обратите внимание, что, начиная с версии драйвера JDBC 2.0, свойство соединения responseBuffering по умолчанию имеет значение «adaptive».  
  
 Затем с помощью инструкции SQL с [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) , образец кода выполняет инструкцию SQL и объектов помещает данные, возвращенные в [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
 И, наконец, в примере кода выполняется итерация по строкам данных, содержащихся в результирующем наборе и использует [getCharacterStream](../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md) метод для доступа к некоторые данные, которые она содержит.  
  
 [!code[JDBC#UsingAdaptiveBuffering1](../../connect/jdbc/codesnippet/Java/reading-large-data-sample_1.java)]  
  
## <a name="see-also"></a>См. также:  
 [Работа с большими объемами данных](../../connect/jdbc/working-with-large-data.md)  
  
  


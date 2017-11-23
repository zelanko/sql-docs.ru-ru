---
title: "Обновление больших объемов данных образец | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76ecc05f-a77d-40a2-bab9-91a7fcf17347
caps.latest.revision: "27"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 755759dcca9d8ff7288dafc92c55a69e956e0ced
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="updating-large-data-sample"></a>Образец обновления данных большого объема
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Это [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] образце приложения показано обновления большого столбца в базе данных.  
  
 Файл кода для этого образца имеет имя updateLargeData.java и находится в следующей папке:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \samples\adaptive  
  
## <a name="requirements"></a>Требования  
 Чтобы запустить этот образец приложения, потребуется доступ к [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных. Необходимо также включить в параметр classpath путь к файлу sqljdbc4.jar. Если параметр classpath не включает путь к файлу sqljdbc4.jar, то образец приложения вызовет стандартное исключение «Класс не найден». Дополнительные сведения о том, как задать значение переменной classpath см. в разделе [с помощью драйвера JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Предоставляет sqljdbc.jar, sqljdbc4.jar, sqljdbc41.jar или sqljdbc42.jar файлы библиотек классов для использования в зависимости от выбранных параметров среды выполнения Java (JRE). В этом образце используется [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) и [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) методы, которые были введены в API JDBC 4.0, для доступа к методам буферизации ответов специфические для драйвера. Чтобы скомпилировать и выполнить этот образец, понадобится библиотека классов sqljdbc4.jar, которая обеспечивает работу JDBC 4.0. Дополнительные сведения о какие файлы JAR следует выбрать см. в разделе [требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Пример  
 В следующем примере образец кода устанавливает соединение для [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] базы данных. Затем в примере кода создается объект инструкции и использует [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) метод для проверки, является ли объект инструкции оболочкой для указанного [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класса. [Unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) метод используется для доступа к методам буферизации ответов специфические для драйвера.  
  
 Далее образец кода задает режим буферизации ответов "**адаптивной**» с помощью [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) метод [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класса, а также показано, как получить режим адаптивной буферизации.  
  
 Затем он выполняет инструкцию SQL и помещает данные, возвращенные в обновляемый [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
 Наконец, образец кода выполняет проход по строкам данных, содержащимся в результирующем наборе. При обнаружении пустой документ сводки, он использует сочетание [updateString](../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md) и [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) методы для обновления строки данных и ее сохранения в базу данных. Если данные уже существует, он использует [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) метод для отображения некоторых данных, которые она содержит.  
  
 По умолчанию драйвера "**адаптивной.**» Однако, для однопроходных обновляемых результирующих наборов и если данные в результирующем наборе больше, чем память приложения, приложение должно задать адаптивный режим буферизации явным образом с помощью [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) метод [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класса.  
  
 [!code[JDBC#UsingAdaptiveBuffering3](../../connect/jdbc/codesnippet/Java/updating-large-data-sample_1.java)]  
  
## <a name="see-also"></a>См. также:  
 [Работа с большими объемами данных](../../connect/jdbc/working-with-large-data.md)  
  
  

---
title: Чтение больших объемов данных образец | Документация Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6c986144-3854-4352-8331-e79eccbefc28
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 51f1925c55fc3ece88aa8354afb181af8aec38ce
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278645"
---
# <a name="reading-large-data-sample"></a>Образец считывания данных большого объема
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В этом примере приложения, использующем драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], показано, как получить из базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] большое значение одного столбца с помощью метода [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md).  
  
 Файл кода для этого образца имеет имя ReadLargeData.java и находится в следующей папке:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \samples\adaptive  
  
## <a name="requirements"></a>Требования  
 Для запуска этого образца приложения также потребуется доступ к образцу базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Также можно задайте параметр Classpath путь к JAR-файл mssql-jdbc. Дополнительные сведения о том, как путь к классу см. в разделе [с помощью драйвера JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] включает файлы библиотек классов mssql-jdbc, которые используются в зависимости от выбранных параметров среды выполнения Java (JRE). Дополнительные сведения о какие файлы JAR следует выбрать, см. в разделе [требования к системе для драйвера JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Пример  
 В следующем примере образец кода будет использоваться для соединения с базой данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Затем образец кода создает образцы данных и обновляет таблицу Production.Document с помощью параметризированного запроса.  
  
 Кроме того, в образце кода показано, как получить режим адаптивной буферизации с помощью метода [getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) класса [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md). Обратите внимание, что, начиная с версии драйвера JDBC 2.0, свойство соединения responseBuffering по умолчанию имеет значение «adaptive».  
  
 Затем в образце кода выполняется инструкция SQL с объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), а возвращенные ею данные помещаются в объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
 Наконец, выполняется проход по строкам данных, содержащимся в результирующем наборе, и выполняется доступ к некоторым из этих данных с помощью метода [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md).  
  
 [!code[JDBC#UsingAdaptiveBuffering1](../../../connect/jdbc/codesnippet/Java/reading-large-data-sample_1.java)]  
  
## <a name="see-also"></a>См. также:  
 [Работа с большими объемами данных](../../../connect/jdbc/working-with-large-data.md)  
  
  

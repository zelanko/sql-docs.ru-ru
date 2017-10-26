---
title: "Поддержка национального набора символов | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fceacfd-df4f-40cd-b7a2-5e5e58a5979f
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f143d37911a1375a1eebe9de04c8b509817575ec
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="national-character-set-support"></a>Поддержка национального набора символов
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Драйвер JDBC реализует поддержку API JDBC 4.0, которая включает новые методы API преобразования национальных наборов символов. Эта поддержка включает в себя новые методы задания, считывания и обновления для **NCHAR**, **NVARCHAR**, **LONGNVARCHAR**, и **NCLOB** типов JDBC.  
  
 Далее приведен список новых методов считывания, задания и обновления для поддержки преобразования национальной кодировки.  
  
-   [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md): [setNString](../../connect/jdbc/reference/setnstring-method-int-java-lang-string.md), [setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md), [setNClob](../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md).  
  
-   [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md): [getNClob](../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md), [getNString](../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md), [getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md), [setNString](../../connect/jdbc/reference/setnstring-method-sqlservercallablestatement.md), [setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md), [setNClob](../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md).  
  
-   [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md): [getNClob](../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md), [getNString](../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md), [getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md), [updateNClob](../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md), [updateNString](../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md), [updateNCharacterStream](../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md).  
  
> [!NOTE]  
>  Для использования этих методов в приложении необходимо задать путь к классу, включающий файл sqljdbc4.jar.  
  
 Для отправки строковых параметров на сервер в Юникоде, приложения должны использовать новые методы национальных кодировок JDBC 4.0; или задайте **sendStringParametersAsUnicode** свойства соединения»**true**» при использовании методов ненациональных символов. Рекомендуется по возможности использовать новые методы национальных кодировок JDBC 4.0. Дополнительные сведения о **sendStringParametersAsUnicode** свойства соединения в разделе [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  


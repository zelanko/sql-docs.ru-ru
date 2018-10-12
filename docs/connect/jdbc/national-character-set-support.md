---
title: Поддержка национального набора символов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4fceacfd-df4f-40cd-b7a2-5e5e58a5979f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0767cdbd57a481ebe82993f3be4ae3e8e1738c31
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47683202"
---
# <a name="national-character-set-support"></a>Поддержка национального набора символов
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Драйвер JDBC реализует поддержку API JDBC 4.0, которая включает новые методы API преобразования национальных наборов символов. Эта поддержка включает новые методы задания, считывания и обновления для **NCHAR**, **NVARCHAR**, **LONGNVARCHAR**, и **NCLOB** типы JDBC.  
  
 Далее приведен список новых методов считывания, задания и обновления для поддержки преобразования национальной кодировки.  
  
-   [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md): [setNString](../../connect/jdbc/reference/setnstring-method-int-java-lang-string.md), [setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md), [setNClob](../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md).  
  
-   [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md): [getNClob](../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md), [getNString](../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md), [getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md), [setNString](../../connect/jdbc/reference/setnstring-method-sqlservercallablestatement.md), [setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md), [setNClob](../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md).  
  
-   [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md): [getNClob](../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md), [getNString](../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md), [getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md), [updateNClob](../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md), [updateNString](../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md), [updateNCharacterStream](../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md).  
  
> [!NOTE]  
>  Для использования этих методов в приложении необходимо задать путь к классу, включающий файл sqljdbc4.jar.  
  
 Для отправки строковых параметров на сервер в формате Юникода приложения должны использовать новые методы национальных кодировок JDBC 4.0 или установить свойство соединения **sendStringParametersAsUnicode** в значение **true** при использовании других методов. Рекомендуется по возможности использовать новые методы национальных кодировок JDBC 4.0. Дополнительные сведения о **sendStringParametersAsUnicode** свойство подключения, см. в разделе [заданию свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  

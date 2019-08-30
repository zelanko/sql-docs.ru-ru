---
title: Поддержка национальных наборов символов | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4fceacfd-df4f-40cd-b7a2-5e5e58a5979f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ae20e40723822da0004b82dd7c89961fa0448e10
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69027874"
---
# <a name="national-character-set-support"></a>Поддержка национального набора символов
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Драйвер JDBC реализует поддержку API JDBC 4.0, которая включает новые методы API преобразования национальных наборов символов. Эта поддержка включает в себя новые методы задания, считывания и обновления для типов JDBC, **NCHAR**, **nvarchar**, **лонгнварчар**и **NCLOB** .  
  
 Далее приведен список новых методов считывания, задания и обновления для поддержки преобразования национальной кодировки.  
  
-   [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md): [setNString](../../connect/jdbc/reference/setnstring-method-int-java-lang-string.md), [setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md), [setNClob](../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md).  
  
-   [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md): [getNClob](../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md), [getNString](../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md), [getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md), [setNString](../../connect/jdbc/reference/setnstring-method-sqlservercallablestatement.md), [setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md), [setNClob](../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md).  
  
-   [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md): [getNClob](../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md), [getNString](../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md), [getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md), [updateNClob](../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md), [updateNString](../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md), [updateNCharacterStream](../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md).  
  
> [!NOTE]  
>  Для использования этих методов в приложении необходимо задать путь к классу, включающий файл sqljdbc4.jar.  
  
 Для отправки строковых параметров на сервер в формате Юникода приложения должны использовать новые методы национальных кодировок JDBC 4.0 или установить свойство соединения **sendStringParametersAsUnicode** в значение **true** при использовании других методов. Рекомендуется по возможности использовать новые методы национальных кодировок JDBC 4.0. Дополнительные сведения о свойстве соединения **sendStringParametersAsUnicode** см. [в разделе Задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>См. также раздел  
 [Основные сведения о типах данных JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  

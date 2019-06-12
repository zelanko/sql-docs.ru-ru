---
title: Интерфейс ISQLServerResultSet | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 002496f7-8ec0-4267-b4e6-ba095e2ef306
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6a5332a31da0114eb710befe5ecd62c6821a3295
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796405"
---
# <a name="isqlserverresultset-interface"></a>Интерфейс ISQLServerResultSet
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет результирующий набор JDBC. Этот интерфейс добавлен в версии 3.0 драйвера JDBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширяет**: java.sql.ResultSet  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public interface ISQLServerResultSet  
```  
  
## <a name="remarks"></a>Remarks  
 Этот интерфейс реализуется [класса SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
 Этот интерфейс обеспечивает доступ к следующим методам, определяемым [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
|Метод|Дополнительные сведения см. в разделе|  
|------------|-------------------------------|  
|public microsoft.sql.DateTimeOffset getDateTimeOffset(int)|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-int-sqlserverresultset.md)|  
|public microsoft.sql.DateTimeOffset getDateTimeOffset(String)|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-java-lang-string-sqlserverresultset.md)|  
|public void updateDateTimeOffset(int, microsoft.sql.DateTimeOffset)|[updateDateTimeOffset](../../../connect/jdbc/reference/updatedatetimeoffset-int-microsoft-sql-datetimeoffset-sqlserverresultset.md)|  
|public void updateDateTimeOffset(String, microsoft.sql.DateTimeOffset)|[updateDateTimeOffset](../../../connect/jdbc/reference/updatedatetimeoffset-string-microsoft-sql-datetimeoffset-sqlserverresultset.md)|  
  
 Этот интерфейс обеспечивает доступ к следующим полям, определяемым [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
|Поле|Дополнительные сведения см. в разделе|  
|-----------|-------------------------------|  
|public static final int CONCUR_SS_OPTIMISTIC_CC|[CONCUR_SS_OPTIMISTIC_CC](../../../connect/jdbc/reference/concur-ss-optimistic-cc-field-sqlserverresultset.md)|  
|public static final int CONCUR_SS_OPTIMISTIC_CCVAL|[CONCUR_SS_OPTIMISTIC_CCVAL](../../../connect/jdbc/reference/concur-ss-optimistic-ccval-field-sqlserverresultset.md)|  
|public static final int CONCUR_SS_SCROLL_LOCKS|[CONCUR_SS_SCROLL_LOCKS](../../../connect/jdbc/reference/concur-ss-scroll-locks-field-sqlserverresultset.md)|  
|public static final int TYPE_SS_DIRECT_FORWARD_ONLY|[TYPE_SS_DIRECT_FORWARD_ONLY](../../../connect/jdbc/reference/type-ss-direct-forward-only-field-sqlserverresultset.md)|  
|public static final int TYPE_SS_SCROLL_DYNAMIC|[TYPE_SS_SCROLL_DYNAMIC](../../../connect/jdbc/reference/type-ss-scroll-dynamic-field-sqlserverresultset.md)|  
|public static final int TYPE_SS_SCROLL_KEYSET|[TYPE_SS_SCROLL_KEYSET](../../../connect/jdbc/reference/type-ss-scroll-keyset-field-sqlserverresultset.md)|  
|public static final int TYPE_SS_SCROLL_STATIC|[TYPE_SS_SCROLL_STATIC](../../../connect/jdbc/reference/type-ss-scroll-static-field-sqlserverresultset.md)|  
|public static final int TYPE_SS_SERVER_CURSOR_FORWARD_ONLY|[TYPE_SS_SERVER_CURSOR_FORWARD_ONLY](../../../connect/jdbc/reference/type-ss-server-cursor-forward-only-field-sqlserverresultset.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

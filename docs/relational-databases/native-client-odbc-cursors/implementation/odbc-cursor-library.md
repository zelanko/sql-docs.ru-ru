---
title: "Библиотека курсоров ODBC | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-cursors
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], library
- SQL_CUR_USE_DRIVER option
- ODBC applications, cursors
- ODBC cursors, library
- SQL_CUR_USE_IF_NEEDED option
- SQLSetConnectAttr function
- SQL_CUR_USE_ODBC option
ms.assetid: 3c610d3d-6e06-49cf-9a40-05b6a1c83a32
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e9d1540cab27708bfb01cb210a2f82c771de1d57
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="odbc-cursor-library"></a>Библиотека курсоров ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Некоторые драйверы ODBC поддерживают только параметры курсора по умолчанию; Эти драйверы также не поддерживают позиционированных операций с курсором, таких как **SQLSetPos**. Библиотека курсоров ODBC — компонент доступа к данным MDAC, используемый для реализации блочных или статических курсоров на драйвере, который обычно не поддерживает их. Библиотека курсоров также реализует позиционированные инструкции UPDATE и DELETE и **SQLSetPos** для создаваемых курсоров.  
  
 Библиотека курсоров ODBC реализована как уровень между диспетчером драйверов ODBC и драйвером ODBC. Если библиотека курсоров ODBC загружена, диспетчер драйверов ODBC направляет все относящиеся к курсору команды в библиотеку курсоров, а не драйвер. Библиотека курсоров реализует курсор путем выборки целого результирующего набора из базового драйвера и кэширования результирующего набора на клиенте. При использовании библиотеки курсоров ODBC приложение ограничено функциональностью курсора для библиотеки курсоров; любая дополнительная функциональность базового драйвера недоступна для приложения.  
  
 Нет необходимости использовать библиотеку курсоров ODBC с драйвером ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], так как сам драйвер обеспечивает более широкую функциональность курсора, чем библиотека курсоров ODBC. Единственная причина для использования библиотеки курсоров ODBC с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента вызвано тем, что драйвер поддерживает курсор через серверные курсоры серверные курсоры не поддерживают все инструкции SQL. Всегда, когда необходимо иметь статический курсор с хранимыми процедурами, пакетами или инструкциями SQL, содержащими предложение COMPUTE, COMPUTE BY, FOR BROWSE или INTO, используйте библиотеку курсоров ODBC. Однако при использовании библиотеки курсоров необходима осмотрительность, так как кэширование всего результирующего набора на клиенте может потребовать большого объема памяти и снизить производительность.  
  
 Приложение вызывает библиотеку курсоров для подключения, подключения, используя [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) необходимо установить атрибут соединения SQL_ATTR_ODBC_CURSORS до соединения с источником данных. SQL_ATTR_ODBC_CURSORS устанавливается в одно из трех значений:  
  
 SQL_CUR_USE_ODBC  
 Если этот параметр установлен с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента библиотека курсоров ODBC переопределяет [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента собственную поддержку курсора. Только типы курсора, поддерживаемые библиотекой курсоров, могут быть использованы для соединения; серверные курсоры не могут быть использованы.  
  
 SQL_CUR_USE_DRIVER  
 Если этот параметр установлен, все курсора собственная функциональность [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента можно использовать для подключения. Библиотека курсоров ODBC не может быть использована. Все курсоры реализованы как серверные курсоры.  
  
 SQL_CUR_USE_IF_NEEDED  
 Если задан этот параметр, эффект будет таким же, как при использовании SQL_CUR_USE_DRIVER с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента. Во время подключения диспетчер драйверов ODBC проверяет, поддерживает ли драйвер ODBC, который подключается к параметр sql_fetch_prior функции [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md). Если драйвер не поддерживает параметр, диспетчер драйверов ODBC загружает библиотеку курсоров ODBC. Если драйвер поддерживает параметр, диспетчер драйверов ODBC не загружает библиотеку курсоров ODBC и приложение использует собственную поддержку драйвера. Поскольку [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента поддерживает SQL_FETCH_PRIOR, диспетчер драйверов ODBC не загружает библиотеку курсоров ODBC.  
  
 Библиотека курсоров ODBC позволяет приложениям использовать несколько активных инструкций для соединения, а также прокручиваемые, обновляемые курсоры. Библиотека курсоров должна быть загружена для поддержки этой функциональности. Используйте [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) для указания того, как следует использовать библиотеку курсоров и [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) для указания размера типа, параллелизм и набора строк курсора.  
  
## <a name="see-also"></a>См. также:  
 [Способы реализации курсоров](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  

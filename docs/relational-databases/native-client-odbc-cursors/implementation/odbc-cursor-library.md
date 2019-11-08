---
title: Библиотека курсоров ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eeaef25c0a7c1d09ca3ee52cee2783275aa6133e
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73784720"
---
# <a name="odbc-cursor-library"></a>Библиотека курсоров ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Некоторые драйверы ODBC поддерживают только параметры курсора по умолчанию. Эти драйверы также не поддерживают позиционированные операции с курсорами, такие как **SQLSetPos**. Библиотека курсоров ODBC — компонент доступа к данным MDAC, используемый для реализации блочных или статических курсоров на драйвере, который обычно не поддерживает их. Библиотека курсоров также реализует позиционированные инструкции UPDATE и DELETE и **SQLSetPos** для создаваемых курсоров.  
  
 Библиотека курсоров ODBC реализована как уровень между диспетчером драйверов ODBC и драйвером ODBC. Если библиотека курсоров ODBC загружена, диспетчер драйверов ODBC направляет все относящиеся к курсору команды в библиотеку курсоров, а не драйвер. Библиотека курсоров реализует курсор путем выборки целого результирующего набора из базового драйвера и кэширования результирующего набора на клиенте. При использовании библиотеки курсоров ODBC приложение ограничено функциональностью курсора для библиотеки курсоров; любая дополнительная функциональность базового драйвера недоступна для приложения.  
  
 Нет необходимости использовать библиотеку курсоров ODBC с драйвером ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], так как сам драйвер обеспечивает более широкую функциональность курсора, чем библиотека курсоров ODBC. Единственная причина использования библиотеки курсоров ODBC с драйвером ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] заключается в том, что драйвер реализует поддержку курсора через серверные курсоры, а серверные курсоры не поддерживают все инструкции SQL. Всегда, когда необходимо иметь статический курсор с хранимыми процедурами, пакетами или инструкциями SQL, содержащими предложение COMPUTE, COMPUTE BY, FOR BROWSE или INTO, используйте библиотеку курсоров ODBC. Однако при использовании библиотеки курсоров необходима осмотрительность, так как кэширование всего результирующего набора на клиенте может потребовать большого объема памяти и снизить производительность.  
  
 Приложение вызывает библиотеку курсоров в отдельном соединении с помощью [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) , чтобы задать атрибут подключения SQL_ATTR_ODBC_CURSORS перед подключением к источнику данных. SQL_ATTR_ODBC_CURSORS устанавливается в одно из трех значений:  
  
 SQL_CUR_USE_ODBC  
 Если этот параметр задан с помощью драйвера ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], Библиотека курсоров ODBC пере[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] определяет встроенную поддержку собственного курсора драйвера ODBC для собственного клиента. Только типы курсора, поддерживаемые библиотекой курсоров, могут быть использованы для соединения; серверные курсоры не могут быть использованы.  
  
 SQL_CUR_USE_DRIVER  
 Если этот параметр задан, для подключения можно использовать все функции поддержки курсоров, встроенные в драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Библиотека курсоров ODBC не может быть использована. Все курсоры реализованы как серверные курсоры.  
  
 SQL_CUR_USE_IF_NEEDED  
 Если этот параметр задан, то результат будет таким же, как и SQL_CUR_USE_DRIVER при использовании с драйвером ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Во время подключения диспетчер драйверов ODBC проверяет, поддерживает ли подключенный драйвер ODBC параметр SQL_FETCH_PRIOR [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md). Если драйвер не поддерживает параметр, диспетчер драйверов ODBC загружает библиотеку курсоров ODBC. Если драйвер поддерживает параметр, диспетчер драйверов ODBC не загружает библиотеку курсоров ODBC и приложение использует собственную поддержку драйвера. Так как драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает SQL_FETCH_PRIOR, диспетчер драйверов ODBC не загружает библиотеку курсоров ODBC.  
  
 Библиотека курсоров ODBC позволяет приложениям использовать несколько активных инструкций для соединения, а также прокручиваемые, обновляемые курсоры. Библиотека курсоров должна быть загружена для поддержки этой функциональности. Используйте [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) для указания способа использования библиотеки курсоров и [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) для указания типа курсора, параллелизма и размера набора строк.  
  
## <a name="see-also"></a>См. также раздел  
 [Способы реализации курсоров](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  

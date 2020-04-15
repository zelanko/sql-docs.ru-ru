---
title: Библиотека ОДБК Курсор (ru) Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 93c85bc943d1a6a081cbea6bbeae40ba85aeffc5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305405"
---
# <a name="odbc-cursor-library"></a>Библиотека курсоров ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Некоторые драйверы ODBC поддерживают только настройки курсора по умолчанию; эти драйверы также не поддерживают позиционированные операции курсора, такие как **S'LSetPos.** Библиотека курсоров ODBC — компонент доступа к данным MDAC, используемый для реализации блочных или статических курсоров на драйвере, который обычно не поддерживает их. Библиотека курсора также реализует позиционированные заявления UPDATE и DELETE и **S'LSetPos** для созданных ею курсоров.  
  
 Библиотека курсоров ODBC реализована как уровень между диспетчером драйверов ODBC и драйвером ODBC. Если библиотека курсоров ODBC загружена, диспетчер драйверов ODBC направляет все относящиеся к курсору команды в библиотеку курсоров, а не драйвер. Библиотека курсоров реализует курсор путем выборки целого результирующего набора из базового драйвера и кэширования результирующего набора на клиенте. При использовании библиотеки курсоров ODBC приложение ограничено функциональностью курсора для библиотеки курсоров; любая дополнительная функциональность базового драйвера недоступна для приложения.  
  
 Нет необходимости использовать библиотеку курсоров ODBC с драйвером ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], так как сам драйвер обеспечивает более широкую функциональность курсора, чем библиотека курсоров ODBC. Единственная причина использования библиотеки курсоров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC ODBC native Client заключается в том, что драйвер выполняет поддержку курсора через курсоры серверов, а курсоры серверов не поддерживают все операторы S'L. Всегда, когда необходимо иметь статический курсор с хранимыми процедурами, пакетами или инструкциями SQL, содержащими предложение COMPUTE, COMPUTE BY, FOR BROWSE или INTO, используйте библиотеку курсоров ODBC. Однако при использовании библиотеки курсоров необходима осмотрительность, так как кэширование всего результирующего набора на клиенте может потребовать большого объема памяти и снизить производительность.  
  
 Приложение вызывает библиотеку курсора на основе подключения, используя [S'LSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) для установки атрибута SQL_ATTR_ODBC_CURSORS соединения перед подключением к источнику данных. SQL_ATTR_ODBC_CURSORS устанавливается в одно из трех значений:  
  
 SQL_CUR_USE_ODBC  
 Когда эта опция [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] установлена с драйвером Native Client ODBC, библиотека [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] курсора ODBC переопределяет поддержку родного клиента ODBC. Только типы курсора, поддерживаемые библиотекой курсоров, могут быть использованы для соединения; серверные курсоры не могут быть использованы.  
  
 SQL_CUR_USE_DRIVER  
 При установке этой опции для подключения можно [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использовать всю поддержку курсора, родную для драйвера Native Client ODBC. Библиотека курсоров ODBC не может быть использована. Все курсоры реализованы как серверные курсоры.  
  
 SQL_CUR_USE_IF_NEEDED  
 При установке этой опции эффект такой же, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] как и SQL_CUR_USE_DRIVER при использовании с драйвером Native Client ODBC. Во время подключения менеджер драйвера ODBC тестирует, поддерживает ли драйвер ODBC SQL_FETCH_PRIOR опцию [S'LFetchScroll.](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) Если драйвер не поддерживает параметр, диспетчер драйверов ODBC загружает библиотеку курсоров ODBC. Если драйвер поддерживает параметр, диспетчер драйверов ODBC не загружает библиотеку курсоров ODBC и приложение использует собственную поддержку драйвера. Поскольку [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер Native Client ODBC поддерживает SQL_FETCH_PRIOR, диспетчер драйверов ODBC не загружает библиотеку курсора ODBC.  
  
 Библиотека курсоров ODBC позволяет приложениям использовать несколько активных инструкций для соединения, а также прокручиваемые, обновляемые курсоры. Библиотека курсоров должна быть загружена для поддержки этой функциональности. Для указания того, как следует использовать библиотеку курсоров, и sLSetStmtAttr для указания типа курсора, параллелизма и размера строки— [«SLSetStmtAttr» и «SLSetStmtAttr».](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)  
  
## <a name="see-also"></a>См. также:  
 [Способы реализации курсоров](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  

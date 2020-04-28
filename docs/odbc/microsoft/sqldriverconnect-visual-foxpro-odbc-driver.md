---
title: SQLDriverConnect (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 10492c8f-3a18-4971-9db8-879e878083b9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e270f8c9be42dc109adeaa49acb84f29f2b9511
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307095"
---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полная  
  
 Соответствие API ODBC: уровень 1  
  
 Подключается к существующему источнику данных, который может быть либо [базой данных](../../odbc/microsoft/visual-foxpro-terminology.md) , либо каталогом [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md). Ключевые слова "Attribute" ODBC "UID" и "PWD" игнорируются. В следующей таблице перечислены дополнительные поддерживаемые ключевые слова атрибутов.  
  
|Ключевое слово атрибута ODBC|Значение атрибута|  
|----------------------------|---------------------|  
|DSN||  
|ИД пользователя|Игнорируется драйвером ODBC для Visual FoxPro, но не создает ошибку.|  
|PWD|Игнорируется драйвером ODBC для Visual FoxPro, но не создает ошибку.|  
|Драйвер|Имя и расположение драйвера ODBC для Visual FoxPro; реализуется диспетчером драйверов.|  
  
|Ключевое слово атрибута ODBC Driver для Visual FoxPro|Значение атрибута|  
|-------------------------------------------------|---------------------|  
|баккграундфетч|"Yes" или "No"|  
|Разобрать по копиям|"Machine" или другой последовательности сортировки. Список поддерживаемых последовательностей сортировки см. в разделе [Set COLLATE](../../odbc/microsoft/set-collate-command.md).|  
|Описание||  
|Монопольная блокировка|"Yes" или "No"|  
|SourceDB|Полный путь к каталогу, содержащему нуль или более [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md), либо абсолютный путь и имя файла для [базы данных](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|Тип источника|"DBC" или "DBF"|  
|Версия||  
  
 Если имя источника данных не указано, диспетчер драйверов запрашивает у пользователя сведения (в зависимости от значения аргумента *фдриверкомплетион* ), а затем продолжит. Если требуются дополнительные сведения, драйвер ODBC для Visual FoxPro отображает диалоговое окно запроса.  
  
 Дополнительные сведения см. в разделе [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) в *справочнике программиста по ODBC*.

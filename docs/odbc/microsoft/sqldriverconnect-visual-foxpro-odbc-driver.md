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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dc0bcf6a191f67b87b422b17778f56feda1f5227
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63238081"
---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: Полное  
  
 Соответствие API ODBC: уровне 1  
  
 Подключается к существующего источника данных, который может представлять собой [базы данных](../../odbc/microsoft/visual-foxpro-terminology.md) или каталог [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md). Ключевые слова ODBC атрибута UID и PWD игнорируются. В следующей таблице перечислены ключевые слова дополнительных поддерживаемых атрибутов.  
  
|Ключевое слово атрибута ODBC|Значение атрибута|  
|----------------------------|---------------------|  
|DSN||  
|UID|Учитывается драйвером ODBC для Visual FoxPro, но не создается ошибка.|  
|PWD|Учитывается драйвером ODBC для Visual FoxPro, но не создается ошибка.|  
|Драйвер|Имя и расположение драйвера ODBC для Visual FoxPro; реализован диспетчером драйверов.|  
  
|Слово атрибута Visual FoxPro драйвер ODBC|Значение атрибута|  
|-------------------------------------------------|---------------------|  
|BackgroundFetch|«Yes» или «No»|  
|Разобрать по копиям|«Машина» или другие упорядоченной последовательности. Список поддерживаемых упорядоченной последовательности, см. в разделе [ЗАДАТЬ COLLATE](../../odbc/microsoft/set-collate-command.md).|  
|Описание||  
|Монопольно|«Yes» или «No»|  
|SourceDB|Полный путь к каталогу, содержащему ноль или более [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md), или абсолютный путь и имя файла для [базы данных](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|Тип источника|«DBC» или «DBF»|  
|Version||  
  
 Если имя источника данных не указан, the Driver Manager запрашивает у пользователя сведения (в зависимости от параметра *fDriverCompletion* аргумент), а затем продолжает. Если требуются дополнительные сведения, драйвер ODBC для Visual FoxPro Отображение диалогового окна запроса.  
  
 Дополнительные сведения см. в разделе [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) в *Справочник по программированию ODBC*.

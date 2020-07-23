---
title: Типы данных, поддерживаемые соединителем для Oracle (Майкрософт) | Документация Майкрософт
ms.custom: ''
ms.date: 08/14/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: chugugrace
ms.author: chugu
ms.openlocfilehash: abbcea42546421fb7c0d3fef9824ef8ef56d2a0c
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86913790"
---
# <a name="microsoft-connector-for-oracle-data-type-support"></a>Типы данных, поддерживаемые соединителем для Oracle (Майкрософт)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

Компоненты SSIS для Oracle поддерживают не все типы данных Oracle. При разработке пакетов в SSDT для столбцов с неподдерживаемыми типами данных будет отображаться предупреждение. Такие столбцы также будут удалены из сопоставления столбцов. Нельзя загрузить данные в столбец с неподдерживаемым типом данных.

## <a name="data-type-mapping"></a>Сопоставление типов данных

В следующей таблице приведены типы данных базы данных Oracle и их стандартное сопоставление с типами данных служб SSIS. В таблице также приведены неподдерживаемые типы данных Oracle.

|Тип данных базы данных Oracle|Тип данных служб SSIS|Комментарии|
|:-|:-|:-|
|VARCHAR2|DT_STR||
|NVARCHAR2|DT_WSTR||
|CHAR|DT_STR||
|NUMBER|DT_R8|Можно изменить на DT_NUMERIC с определенной точностью и масштабом. Точность и масштаб определяются пользователем в соответствии с требованиями. Выходные данные будут представлять данные столбца в виде числа с фиксированной точностью и масштабом.|
|NUMBER(P, S)| Если масштаб равен 0 в соответствии с точностью (P). <li> DT_I1 <Li> DT_I2 <Li> DT_I4 <Li> DT_NUMBERIC(P,0)||
||DT_NUMERIC(P,S)||
|DATE|DT_DBTIMESTAMP||
|<li>timestamp <li>TIMESTAMP WITH TIME ZONE <li>INTERVAL YEAR TO MONTH <li>INTERVAL DAY TO SECOND <li>TIMESTAMP WITH LOCAL TIME ZONE|DT_STR||
|RAW|DT_BYTES||
|CLOB|DT_TEXT|Типы данных CLOB, NCLOB и BLOB поддерживаются только в режиме массива, но не в режиме быстрой загрузки.|
|NCLOB|DT_NTEXT||
|BLOB|DT_IMAGE||
|UROWID|Не поддерживается||
|REF|Не поддерживается||
|BFILE|Не поддерживается||
|LONG|Не поддерживается||
|LONG RAW|Не поддерживается||
|ROWID|Не поддерживается||
|Пользовательский тип (тип объекта, VARRAY, вложенная таблица)|Не поддерживается||

## <a name="next-steps"></a>Дальнейшие действия

- Настройка [диспетчера подключений Oracle](oracle-connection-manager.md).
- Настройка [источника Oracle](oracle-source.md).
- Настройка [назначения Oracle](oracle-destination.md).
- Если у вас возникнут вопросы, посетите страницу [технического сообщества](https://aka.ms/AA5u35j).

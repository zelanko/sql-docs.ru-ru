---
title: Эмуляция переменных пакета Oracle
description: Описывает, как Помощник по миграции SQL Server (SSMA) для Oracle эмулирует переменные пакета Oracle в SQL Server.
authors: nahk-ivanov
ms.service: ssma
ms.devlang: sql
ms.topic: article
ms.date: 1/22/2020
ms.author: alexiva
ms.openlocfilehash: 9a8ca5c7dfdda98e1c005c3851d061957cf67449
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "76762828"
---
# <a name="emulating-oracle-package-variables"></a>Эмуляция переменных пакета Oracle

Oracle поддерживает инкапсуляцию переменных, типов, хранимых процедур и функций в пакет. При преобразовании пакетов Oracle необходимо преобразовать:

* Процедуры и функции — как открытые, так и частные
* Переменные
* Курсоры
* Процедуры инициализации

В этой статье описывается, как Помощник по миграции SQL Server (SSMA) для Oracle преобразует переменные пакета в SQL Server.

## <a name="conversion-basics"></a>Основы преобразования

Для хранения переменных пакета SSMA для Oracle использует хранимые процедуры, которые находятся в специальной `ssma_oracle` схеме вместе с `ssma_oracle.db_storage` таблицей. Эта таблица фильтруется по `SPID` (идентификатору сеанса) и времени входа. Эта фильтрация позволяет различать переменные различных сеансов.

В начале каждой преобразованной процедуры пакета SSMA помещает вызов в `ssma_oracle.db_check_init_package` специальную процедуру, которая проверяет, инициализирован ли пакет, и при необходимости инициализирует его. Каждая процедура инициализации очищает таблицу хранения и задает значения по умолчанию для каждой переменной пакета.

## <a name="example"></a>Пример

Рассмотрим следующий пример преобразования нескольких переменных пакета:

```sql
CREATE OR REPLACE PACKAGE MY_PACKAGE
IS
    space varchar(1) := ' ';
    unitname varchar(128) := 'My Simple Package';
    ts date := sysdate;
END;
```

SSMA преобразует его в следующий код Transact-SQL:

```sql
CREATE PROCEDURE dbo.MY_PACKAGE$SSMA_Initialize_Package
AS
BEGIN
    EXECUTE ssma_oracle.db_clean_storage

    EXECUTE ssma_oracle.set_pv_varchar
        DB_NAME(),
        'DBO',
        'MY_PACKAGE',
        'SPACE',
        ' '

    EXECUTE ssma_oracle.set_pv_varchar
        DB_NAME(),
        'DBO',
        'MY_PACKAGE',
        'UNITNAME',
        'My Simple Package'

    DECLARE
        @temp datetime2

    SET @temp = sysdatetime()

    EXECUTE sysdb.ssma_oracle.set_pv_datetime2
      DB_NAME(),
      'DBO',
      'MY_PACKAGE',
      'TS',
      @temp
END
```

## <a name="emulating-get-and-set-methods-for-package-variables"></a>Эмуляция методов Get и Set для переменных пакета

Oracle использует `Get` методы `Set` и для переменных пакета, чтобы не позволить другим подпрограммам читать и записывать их напрямую. Если существует необходимость сохранения некоторых переменных между вызовами подпрограммы в одном сеансе, эти переменные обрабатываются как глобальные переменные.

Чтобы преодолеть это правило области, SSMA для Oracle использует хранимые процедуры, `ssma_oracle.set_pv_varchar` такие как для каждого типа переменной. Для доступа к этим переменным SSMA использует набор независимых от `get_*` транзакций процедур и `set_*` функций.

| Тип данных в Oracle | Процедура `Set` SSMA           |
| ------------------- | ------------------------------ |
| VARCHAR             | `ssma_oracle.set_pv_varchar`   |
| DATE                | `ssma_oracle.set_pv_datetime2` |
| CHAR                | `ssma_oracle.set_pv_varchar`   |
| INT                 | `ssma_oracle.set_pv_float`     |
| FLOAT               | `ssma_oracle.set_pv_float`     |

Чтобы различать переменные из разных сеансов, SSMA сохраняет переменные вместе с их `SPID` идентификаторами сеанса и временем входа сеанса. Таким же `get_*` процедура `set_*` и сохраняет переменные независимо от сеансов, в которых они выполняются.

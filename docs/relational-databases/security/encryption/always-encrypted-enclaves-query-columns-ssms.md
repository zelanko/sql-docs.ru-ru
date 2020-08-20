---
description: Выполнение запросов к столбцам с помощью Always Encrypted с безопасными анклавами с использованием SSMS
title: Выполнение запросов к столбцам с помощью Always Encrypted с безопасными анклавами с использованием SSMS | Документация Майкрософт
ms.custom: ''
ms.date: 10/31/2019
ms.reviewer: vanto
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 74149cdcf8dd12280103c592c5a8662dddf4e750
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470096"
---
# <a name="query-columns-using-always-encrypted-with-secure-enclaves-with-ssms"></a>Выполнение запросов к столбцам с помощью Always Encrypted с безопасными анклавами с использованием SSMS
[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

В этой статье описывается использование SQL Server Management Studio для выполнения запросов, использующих безопасный серверный анклав, для [Always Encrypted с безопасными анклавами](always-encrypted-enclaves.md), включая:
- Запросы, инициирующие криптографические операции на месте.
- Запросы, инициирующие полнофункциональные вычисления, включая сравнения диапазонов или операции сопоставления шаблонов для столбцов, зашифрованных с помощью ключей с поддержкой анклава.
- Запросы, которые создают или обновляют индексы в зашифрованных столбцах с использованием случайного шифрования и ключей с поддержкой анклава.  

Чтобы использовать SSMS для выполнения запросов к зашифрованным столбцам с помощью безопасного анклава, следуйте инструкциям в статье [Выполнение запросов к столбцам с помощью Always Encrypted с использованием SQL Server Management Studio](always-encrypted-query-columns-ssms.md). При работе с анклавами необходимо иметь в виду следующие моменты.

- Требуется SSMS версии 18.3 или более поздних версий.
- Запросы необходимо отправлять из окна запроса с безопасным анклавом из подключения с включенной функцией Always Encrypted и вычислениями анклава. Подробные инструкции см. в статьях [Руководство. Начало работы с Always Encrypted с безопасными анклавами с использованием SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md) и [Включение и отключение функции Always Encrypted, применяемой для подключения к базе данных](always-encrypted-query-columns-ssms.md#en-dis).

## <a name="next-steps"></a>Next Steps
- [Разработка приложений с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-client-development.md)

## <a name="see-also"></a>См. также  
- [Руководство. Начало работы с Always Encrypted с безопасными анклавами с использованием SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)
- [Настройка шифрования столбцов на месте с помощью Transact-SQL](always-encrypted-enclaves-configure-encryption-tsql.md)
- [Создание и использование индексов в столбцах с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-create-use-indexes.md)


---
description: Выполнение запросов к столбцам с помощью Always Encrypted с безопасными анклавами
title: Выполнение запросов к столбцам с помощью Always Encrypted с безопасными анклавами | Документация Майкрософт
ms.custom: ''
ms.date: 10/31/2019
ms.reviewer: vanto
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15'
ms.openlocfilehash: 517e2a0beb7364507d585d9cd729069048cf1c82
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97477565"
---
# <a name="query-columns-using-always-encrypted-with-secure-enclaves"></a>Выполнение запросов к столбцам с помощью Always Encrypted с безопасными анклавами
[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

В этой статье содержатся общие рекомендации по выполнению запросов к зашифрованным столбцам с помощью безопасного анклава на стороне сервера для [Always Encrypted с безопасными анклавами](always-encrypted-enclaves.md). 

Безопасный анклав используется в следующих типах запросов.
- Запросы, инициирующие криптографические операции на месте с помощью ключей с поддержкой анклава. См. статью [Настройка шифрования столбцов на месте с помощью Transact-SQL](always-encrypted-enclaves-configure-encryption-tsql.md).
- *Расширенные запросы*, инициирующие операции сравнения сопоставления шаблонов для столбцов, зашифрованных с помощью случайного шифрования и ключей с поддержкой анклава.
- Запросы, которые создают или обновляют индексы в зашифрованных столбцах с использованием случайного шифрования и ключей с поддержкой анклава. Дополнительные сведения см. в статье [Создание и использование индексов в столбцах с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-create-use-indexes.md).

> [!NOTE]
> Расширенные запросы и индексы поддерживаются только в столбцах с поддержкой анклава (столбцы, зашифрованные с помощью ключей шифрования столбцов с поддержкой анклава), которые используют случайное шифрование. Детерминированное шифрование не поддерживает расширенные запросы или индексы.

> [!NOTE]
> Для выполнения расширенных запросов к зашифрованным символьным столбцам требуется, чтобы столбцы использовали параметры сортировки с порядком сортировки binary2 (BIN2). 


## <a name="next-steps"></a>Next Steps
- [Выполнение запросов к столбцам с помощью Always Encrypted с безопасными анклавами с использованием SSMS](always-encrypted-enclaves-query-columns-ssms.md)

## <a name="see-also"></a>См. также
- [Руководство. Начало работы с Always Encrypted с безопасными анклавами с использованием SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)


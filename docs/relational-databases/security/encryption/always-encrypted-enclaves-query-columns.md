---
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
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: bf127e7aa40e538bb3dee390f3661ae5d74413f3
ms.sourcegitcommit: 620a868e623134ad6ced6728ce9d03d7d0038fe0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87411500"
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

## <a name="see-also"></a>См. также:
- [Руководство. Начало работы с Always Encrypted с безопасными анклавами с использованием SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)


---
description: Основные сведения о блокировке строк
title: Сведения о блокировке строк | Документация Майкрософт
ms.custom: ''
ms.date: 12/08/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 63c76a2f-f2b9-461f-8904-acbda0169ac3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e5305f3feaa80d0a83dd1e7bfd97088492608ae5
ms.sourcegitcommit: 7f76975c29d948a9a3b51abce564b9c73d05dcf0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96901064"
---
# <a name="understanding-row-locking"></a>Основные сведения о блокировке строк

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] использует блокировки строк [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. С помощью таких блокировок реализуется управление параллелизмом между несколькими пользователями, одновременно вносящими изменения в базу данных. По умолчанию управление транзакциями и блокировками ведется в рамках соединения. Например, если приложение открывает два соединения JDBC, то блокировки, установленные одним соединением, не могут совмещаться с другим соединением. Ни одно из соединений не может устанавливать блокировки, которые вызывают конфликт с блокировкам, удерживаемыми другим соединением.

> [!NOTE]  
> Если используется блокировка строк, то блокируются все строки в буфере выборки, поэтому задание очень большого размера выборки может отрицательно сказаться на параллелизме.

Блокировка обеспечивает целостность транзакций и согласованность базы данных. Блокировка не позволяет пользователям считывать данные, которые изменяются другими пользователями, а также исключает одновременное изменение одних и тех же данных несколькими пользователями. Если блокировка не применяется, то данные в базе данных могут утратить логическую верность, и запросы к этим данным могут давать непредвиденные результаты.

> [!NOTE]  
> Дополнительные сведения о блокировке строк в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе ["Блокировки в компоненте [!INCLUDE[ssDE](../../includes/ssde_md.md)]"](../../relational-databases/sql-server-transaction-locking-and-row-versioning-guide.md#Lock_Engine) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="see-also"></a>См. также раздел

[Управление результирующими наборами с помощью JDBC Driver](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)

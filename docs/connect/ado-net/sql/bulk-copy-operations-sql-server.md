---
title: Операции массового копирования в SQL Server
description: Описание возможности массового копирования для поставщика данных .NET Framework для SQL Server.
ms.date: 09/30/2019
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: c827ae70d9aa344f52de1d76c482beaef90c09aa
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "78897034"
---
# <a name="bulk-copy-operations-in-sql-server"></a>Операции массового копирования в SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Microsoft SQL Server включает популярную служебную программу командной строки **bcp**, позволяющую быстро выполнять массовое копирование больших файлов в таблицы или представления баз данных SQL Server. Класс <xref:Microsoft.Data.SqlClient.SqlBulkCopy> позволяет создавать решения с управляемым кодом, которые предоставляют аналогичные возможности. Существуют другие способы загрузки данных в таблицу SQL Server (например, с помощью инструкции INSERT), но <xref:Microsoft.Data.SqlClient.SqlBulkCopy> делает это значительно быстрее.  
  
Класс <xref:Microsoft.Data.SqlClient.SqlBulkCopy> предоставляет следующие возможности:  
  
- одну операцию массового копирования;  
  
- несколько операций массового копирования;  
  
- операцию массового копирования в транзакции.  
  
> [!NOTE]
>  При использовании платформы .NET Framework 1.1 или более ранней версии (не поддерживающей класс <xref:Microsoft.Data.SqlClient.SqlBulkCopy>) инструкцию SQL Server Transact-SQL **BULK INSERT** можно выполнить при помощи объекта <xref:Microsoft.Data.SqlClient.SqlCommand>.  
  
## <a name="in-this-section"></a>В этом разделе  
[Пример настройки массового копирования](bulk-copy-example-setup.md)  
Описание таблиц, используемых в примерах с массовым копированием, и примеры скриптов SQL для создания таблиц в базе данных AdventureWorks.  
  
[Одинарные операции массового копирования](single-bulk-copy-operations.md)  
Описание процессов одного массового копирования данных в экземпляр SQL Server с помощью класса <xref:Microsoft.Data.SqlClient.SqlBulkCopy>, а также массового копирования с помощью инструкций Transact-SQL и класса <xref:Microsoft.Data.SqlClient.SqlCommand>.  
  
[Несколько операций массового копирования](multiple-bulk-copy-operations.md)  
Описание выполнения нескольких операций массового копирования данных в экземпляр SQL Server с помощью класса <xref:Microsoft.Data.SqlClient.SqlBulkCopy>.  
  
[Транзакции и операции массового копирования](transaction-bulk-copy-operations.md)  
Сведения о том, как выполнить операцию массового копирования в рамках транзакции, в том числе как зафиксировать или откатить эту транзакцию.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [SQL Server и ADO.NET](index.md)

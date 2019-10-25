---
title: Операции массового копирования в SQL Server
description: Описание возможности массового копирования для поставщика данных .NET Framework для SQL Server.
ms.date: 09/30/2019
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 70eed483eb7cb857e23b110b7149badff14ab46f
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452291"
---
# <a name="bulk-copy-operations-in-sql-server"></a>Операции массового копирования в SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Microsoft SQL Server включает популярную служебную программу командной строки **bcp**, позволяющую быстро выполнять массовое копирование больших файлов в таблицы или представления баз данных SQL Server. Класс <xref:Microsoft.Data.SqlClient.SqlBulkCopy> позволяет создавать решения для управляемого кода, которые предоставляют аналогичные функциональные возможности. Существуют другие способы загрузки данных в таблицу SQL Server (например, с помощью инструкции INSERT), но <xref:Microsoft.Data.SqlClient.SqlBulkCopy> делает это значительно быстрее.  
  
С помощью класса <xref:Microsoft.Data.SqlClient.SqlBulkCopy> можно выполнять следующие действия:  
  
- одну операцию массового копирования;  
  
- несколько операций массового копирования;  
  
- операцию массового копирования в транзакции.  
  
> [!NOTE]
>  При использовании платформы .NET Framework 1.1 или более ранней версии (не поддерживающей класс <xref:Microsoft.Data.SqlClient.SqlBulkCopy>) инструкцию SQL Server Transact-SQL **BULK INSERT** можно выполнить при помощи объекта <xref:Microsoft.Data.SqlClient.SqlCommand>.  
  
## <a name="in-this-section"></a>В этом разделе  
[Пример настройки массового копирования](bulk-copy-example-setup.md)  
Описывает таблицы, используемые в примерах с массовым копированием, и предоставляет скрипты SQL для создания таблиц в базе данных AdventureWorks.  
  
[Одинарные операции массового копирования](single-bulk-copy-operations.md)  
Описывает, как выполнить одно групповое копирование данных в экземпляр SQL Server с помощью класса <xref:Microsoft.Data.SqlClient.SqlBulkCopy> и как выполнить операцию копирования с помощью инструкций Transact-SQL и класса <xref:Microsoft.Data.SqlClient.SqlCommand>.  
  
[Несколько операций массового копирования](multiple-bulk-copy-operations.md)  
Описывает, как выполнить несколько операций с массовым копированием данных в экземпляр SQL Server с помощью класса <xref:Microsoft.Data.SqlClient.SqlBulkCopy>.  
  
[Транзакции и операции массового копирования](transaction-bulk-copy-operations.md)  
Описывает, как выполнить операцию с массовым копированием в рамках транзакции, в том числе как зафиксировать или откатить транзакцию.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [SQL Server и ADO.NET](index.md)

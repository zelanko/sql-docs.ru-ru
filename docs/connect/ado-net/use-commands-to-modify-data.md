---
title: Использование команд для изменения данных
description: Описывается использование поставщика данных для выполнения хранимых процедур или инструкций языка описания данных DDL.
ms.date: 11/25/2020
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 98127e41b5b07c38030ef27214c9c92bf7c4b4be
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761482"
---
# <a name="using-commands-to-modify-data"></a>Использование команд для изменения данных

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

С помощью поставщика данных Microsoft SqlClient для SQL Server можно выполнять хранимые процедуры или инструкции языка описания данных (например, CREATE TABLE и ALTER COLUMN) для операций со схемой в базе данных или каталоге. Эти команды не возвращают строки, как это делают запросы, так что для их обработки объект <xref:Microsoft.Data.SqlClient.SqlCommand> предоставляет <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>.

Помимо использования **ExecuteNonQuery** для изменения схемы, этот метод можно также использовать для обработки инструкций SQL (например, INSERT, UPDATE и DELETE), которые изменяют данные, но не возвращают строки.

Хотя метод **ExecuteNonQuery** не возвращает строки, входные и выходные параметры, а также возвращаемые значения могут передаваться и возвращаться через коллекцию **Parameters** объекта **Command**.

## <a name="in-this-section"></a>В этом разделе

[Обновление данных в источнике данных](update-data-inside-data-source.md)  
Описывает выполнение команд или хранимых процедур, которые изменяют данные в базе данных.

[Выполнение операций с каталогами](perform-catalog-operations.md)  
Описывает выполнение команд, которые изменяют схему базы данных.

## <a name="see-also"></a>См. также

- [Извлечение и изменение данных в ADO.NET](retrieving-modifying-data.md)
- [Команды и параметры](commands-parameters.md)
- [Microsoft ADO.NET для SQL Server](microsoft-ado-net-sql-server.md)

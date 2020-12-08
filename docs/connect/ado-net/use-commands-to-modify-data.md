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
ms.openlocfilehash: 03ebdbdd15adfae8e765964e8338f043999319f3
ms.sourcegitcommit: debaff72dbfae91b303f0acd42dd6d99e03135a2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96428296"
---
# <a name="using-commands-to-modify-data"></a>Использование команд для изменения данных

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

С помощью поставщика данных Microsoft SqlClient для SQL Server можно выполнять хранимые процедуры или инструкции языка описания данных (например, CREATE TABLE и ALTER COLUMN) для операций со схемой в базе данных или каталоге. Эти команды не возвращают строки, как это делают запросы, так что для их обработки объект <xref:Microsoft.Data.SqlClient.SqlCommand> предоставляет <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>.

Помимо использования **ExecuteNonQuery** для изменения схемы, этот метод можно также использовать для обработки инструкций SQL (например, INSERT, UPDATE и DELETE), которые изменяют данные, но не возвращают строки.

Хотя метод **ExecuteNonQuery** не возвращает строки, входные и выходные параметры, а также возвращаемые значения могут передаваться и возвращаться через коллекцию **Parameters** объекта **Command**.

## <a name="in-this-section"></a>В этом разделе

[Обновление данных в источнике данных](update-data-inside-data-source.md) Инструкции по выполнению команд или хранимых процедур, позволяющих изменить данные в базе данных.

[Выполнение операций с каталогами](perform-catalog-operations.md) Инструкции по выполнению команд, позволяющих изменить схему базы данных.

## <a name="see-also"></a>См. также

- [Извлечение и изменение данных в ADO.NET](retrieving-modifying-data.md)
- [Команды и параметры](commands-parameters.md)

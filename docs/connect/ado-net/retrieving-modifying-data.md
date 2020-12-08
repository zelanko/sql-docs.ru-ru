---
title: Извлечение и изменение данных
description: В .NET Framework поставщик данных Microsoft SqlClient для SQL Server выступает в качестве моста между приложением и источником данных для считывания и обновления данных.
ms.date: 11/13/2020
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 8fc6a8ed3cf4fec9b97b81c38fb1667588623ba7
ms.sourcegitcommit: debaff72dbfae91b303f0acd42dd6d99e03135a2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419755"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Извлечение и изменение данных в ADO.NET

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Основной функцией любого приложения базы данных является соединение с источником данных и извлечение данных, которые он содержит. Поставщик данных SqlClient обеспечивает взаимодействие между приложением и источником данных, позволяя выполнять команды и получать данные с помощью **DataReader** или **DataAdapter**. Ключевой функцией любого приложения базы данных является возможность обновления данных, хранимых в базе данных. В поставщике данных Microsoft SqlClient для SQL Server обновление данных включает использование **DataAdapter** и <xref:System.Data.DataSet>, а также объектов **Command**. Обновление может включать использование транзакций.

## <a name="in-this-section"></a>В этом разделе

[Подключение к источнику данных](connecting-to-data-source.md). Инструкции по установке подключения к источнику данных и работе с событиями подключения.

[Строки подключений](connection-strings.md). Описание различных аспектов использования строк подключения, в том числе ключевых слов строк подключения и сведений для защиты, а также их хранения и извлечения.

[Организация пулов подключений](connection-pooling.md). Описание объединения подключений в пулы для поставщика данных Microsoft SqlClient для SQL Server.

## <a name="see-also"></a>См. также

- [Сопоставления типов данных в ADO.NET](data-type-mappings-ado-net.md)
- [SQL Server и ADO.NET](./sql/index.md)

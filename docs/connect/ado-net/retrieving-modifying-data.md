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
ms.openlocfilehash: d6e4d6c298c632c446e1671b5d9adabaa19e0776
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761492"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Извлечение и изменение данных в ADO.NET

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Основной функцией любого приложения базы данных является соединение с источником данных и извлечение данных, которые он содержит. Поставщик данных SqlClient обеспечивает взаимодействие между приложением и источником данных, позволяя выполнять команды и получать данные с помощью **DataReader** или **DataAdapter**. Ключевой функцией любого приложения базы данных является возможность обновления данных, хранимых в базе данных. В поставщике данных Microsoft SqlClient для SQL Server обновление данных включает использование **DataAdapter** и <xref:System.Data.DataSet>, а также объектов **Command**. Обновление может включать использование транзакций.

## <a name="in-this-section"></a>В этом разделе

[подключение к источнику данных](connecting-to-data-source.md);  
Описывается установка подключения к источнику данных и работа с событиями подключения.

[Строки подключения](connection-strings.md)  
Содержит разделы, в которых описываются различные аспекты использования строк подключения, в том числе ключевых слов строки подключения, сведения о безопасности, их хранение и извлечение.

[Организация пулов соединений](connection-pooling.md)  
Описание объединения подключений в пулы для поставщика данных Microsoft SqlClient для SQL Server.

[Команды и параметры](commands-parameters.md)  
Содержит разделы, в которых описывается создание команд и построителей команд, настройка параметров и выполнение команд для извлечения и изменения данных.

[Объекты DataAdapter и DataReader](dataadapters-datareaders.md)  
Содержит разделы, в которых описываются объекты DataReader, DataAdapter, параметры, обработка событий объекта и выполнение пакетных операций.

## <a name="see-also"></a>См. также

- [Сопоставления типов данных в ADO.NET](data-type-mappings-ado-net.md)
- [SQL Server и ADO.NET](./sql/index.md)
- [Microsoft ADO.NET для SQL Server](microsoft-ado-net-sql-server.md)

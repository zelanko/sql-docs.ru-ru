---
title: Подключение к источнику данных
description: Сведения об объектах подключений, используемых для подключения к источникам данных в ADO.NET. Выбранный объект Connection зависит от типа источника данных.
ms.date: 11/13/2020
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: ab6edc2a7090de85e970445cdb2b86d6ed5cb8f2
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96126530"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>Подключение к источнику данных в ADO.NET

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

В поставщике данных Microsoft SqlClient объект **Connection** используется для подключения к определенному источнику данных путем предоставления в строке подключения сведений, необходимых для аутентификации. Используемый объект **Connection** зависит от типа источника данных.

Поставщик данных Microsoft SqlClient для SQL Server включает тип <xref:Microsoft.Data.SqlClient.SqlConnection>, который получен из класса <xref:System.Data.Common.DbConnection>.

## <a name="in-this-section"></a>в этом разделе  

[Установка подключения](establishing-connection.md)\
Описывает использование объекта **Connection** для установки подключения с источником данных.

[События подключений](connection-events.md)\
Описывает использование события **InfoMessage** для получения информационных сообщений из источника данных.

## <a name="see-also"></a>См. также

- [Строки подключения](connection-strings.md)
- [Объединение подключений в пул](connection-pooling.md)

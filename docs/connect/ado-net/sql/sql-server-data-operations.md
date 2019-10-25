---
title: Операции с данными SQL Server в ADO.NET
description: Описание работы с данными в SQL Server. Содержит разделы, посвященные массовым операциям копирования, режиму MARS, асинхронным операциям и возвращающим табличное значение параметрам.
ms.date: 08/15/2019
ms.assetid: b864ebc9-ed8e-4059-85fd-36d9198f5521
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: ed9beea680575bba7fb01fc56af147e20b39218a
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452043"
---
# <a name="sql-server-data-operations-in-adonet"></a>Операции с данными SQL Server в ADO.NET

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

В этом разделе SQL Server описаны функции и функции, характерные для поставщика данных Microsoft SqlClient для SQL Server (<xref:Microsoft.Data.SqlClient>).  
  
## <a name="in-this-section"></a>В этом разделе  
[Операции массового копирования в SQL Server](bulk-copy-operations-sql-server.md)  
Описание возможности массового копирования для поставщика данных .NET Framework для SQL Server.  
  
[Режим MARS](multiple-active-result-sets-mars.md)  
Описывает, как можно открыть несколько <xref:Microsoft.Data.SqlClient.SqlDataReader> в соединении, когда каждый экземпляр <xref:Microsoft.Data.SqlClient.SqlDataReader> запускается из отдельной команды.  
  
[Асинхронные операции](asynchronous-operations.md)  
Описание выполнения асинхронных операций с базой данных при помощи API-интерфейса, который создан по асинхронной модели, используемой платформой .NET Framework.  
  
[Параметры, возвращающие табличные значения](table-valued-parameters.md)  
Описывает, как работать с возвращающими табличные значения параметрами, которые появились в SQL Server 2008.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [SQL Server и ADO.NET](index.md)

---
title: Операции с данными SQL Server в ADO.NET
description: Описание работы с данными в SQL Server. Содержит разделы, посвященные массовым операциям копирования, режиму MARS, асинхронным операциям и возвращающим табличное значение параметрам.
ms.date: 08/15/2019
ms.assetid: b864ebc9-ed8e-4059-85fd-36d9198f5521
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 3f435e44ef6fb7fb7ff777e2b5361482fcde9a98
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75251108"
---
# <a name="sql-server-data-operations-in-adonet"></a>Операции с данными SQL Server в ADO.NET

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

В этом разделе описываются функции и режимы работы SQL Server, характерные для поставщика данных Microsoft SqlClient для SQL Server (<xref:Microsoft.Data.SqlClient>).  
  
## <a name="in-this-section"></a>В этом разделе  
[Операции массового копирования в SQL Server](bulk-copy-operations-sql-server.md)  
Описание возможности массового копирования для поставщика данных .NET Framework для SQL Server.  
  
[Режим MARS](multiple-active-result-sets-mars.md)  
Сведения о том, как можно открыть несколько экземпляров <xref:Microsoft.Data.SqlClient.SqlDataReader> в одном подключении, где каждый экземпляр <xref:Microsoft.Data.SqlClient.SqlDataReader> запускается отдельной командой.  
  
[Асинхронные операции](asynchronous-operations.md)  
Описание выполнения асинхронных операций с базой данных при помощи API-интерфейса, который создан по асинхронной модели, используемой платформой .NET Framework.  
  
[Параметры, возвращающие табличные значения](table-valued-parameters.md)  
Здесь описывается работа с возвращающими табличное значение параметрами, появившимися в SQL Server 2008.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [SQL Server и ADO.NET](index.md)

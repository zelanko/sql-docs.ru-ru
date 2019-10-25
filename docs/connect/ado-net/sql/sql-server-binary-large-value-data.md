---
title: Двоичные данные и данные больших значений SQL Server
description: Описание работы с данными больших значений в SQL Server.
ms.date: 08/15/2019
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 0a38d90a810f9ca3ee376562eaabf6e713267b27
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452049"
---
# <a name="sql-server-binary-and-large-value-data"></a>Двоичные данные и данные больших значений SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server предоставляет описатель `max`, который расширяет емкость хранилища `varchar`, `nvarchar` и `varbinary` типов данных. Типы данных `varchar(max)`, `nvarchar(max)` и `varbinary(max)` называются *типами данных большого размера*. Можно использовать типы данных больших значений для хранения 2^31–1 байт данных.  
  
SQL Server 2008 представляет атрибут FILESTREAM, который не является типом данных, а является атрибутом, который может быть определен для столбца, что позволяет хранить данные большого размера в файловой системе, а не в базе данных.  
  
## <a name="in-this-section"></a>В этом разделе  
[Изменение данных больших значений (max) в ADO.NET](modify-large-value-max-data.md)  
Описывает работу с типами данных больших значений.  
  
[Данные файлового потока](filestream-data.md)  
Описывает, как работать с данными большого объема, хранящимися в SQL Server 2008 с помощью атрибута FILESTREAM.  
  
## <a name="next-steps"></a>Следующие шаги
- [Типы данных SQL Server и ADO.NET](sql-server-data-types.md)
- [Операции с данными SQL Server в ADO.NET](sql-server-data-operations.md)

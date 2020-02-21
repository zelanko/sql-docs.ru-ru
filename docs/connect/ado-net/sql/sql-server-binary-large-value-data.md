---
title: Двоичные данные и данные больших значений SQL Server
description: Описание работы с данными больших значений в SQL Server.
ms.date: 08/15/2019
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: e60f8ce6bc8e7ef05a2de942d8bbc2885095d493
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75251127"
---
# <a name="sql-server-binary-and-large-value-data"></a>Двоичные данные и данные больших значений SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server предоставляет описатель `max`, который расширяет возможности хранения для типов данных `varchar`, `nvarchar` и `varbinary`. Типы данных `varchar(max)`, `nvarchar(max)` и `varbinary(max)` называются *типами данных большого размера*. Можно использовать типы данных больших значений для хранения 2^31–1 байт данных.  
  
В SQL Server 2008 добавлен элемент FILESTREAM. Это не тип данных, а определяемый на уровне столбца атрибут, позволяющий хранить данные большого размера в файловой системе, а не в базе данных.  
  
## <a name="in-this-section"></a>В этом разделе  
[Изменение данных больших значений (max) в ADO.NET](modify-large-value-max-data.md)  
Описание работы с типами данных больших значений.  
  
[Данные файлового потока](filestream-data.md)  
Описывает, как работать в SQL Server 2008 с данными большого объема, для которых указан атрибут FILESTREAM.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Типы данных SQL Server и ADO.NET](sql-server-data-types.md)
- [Операции с данными SQL Server в ADO.NET](sql-server-data-operations.md)

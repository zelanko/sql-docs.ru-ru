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
ms.openlocfilehash: 4ed8ccbadb27008fb15d9d117d55b5a4d332a8f6
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896625"
---
# <a name="sql-server-binary-and-large-value-data"></a>Двоичные данные и данные больших значений SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

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

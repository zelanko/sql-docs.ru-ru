---
title: Двоичные данные и данные больших значений SQL Server
description: Описание работы с данными больших значений в SQL Server.
ms.date: 08/15/2019
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 17a38bd45a467625be467f5fb01f0e733f7546bc
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920976"
---
# <a name="sql-server-binary-and-large-value-data"></a>Двоичные данные и данные больших значений SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server предоставляет описатель `max`, который расширяет возможности хранения для типов данных `varchar`, `nvarchar` и `varbinary`. Типы данных `varchar(max)`, `nvarchar(max)` и `varbinary(max)` называются *типами данных большого размера*. Можно использовать типы данных больших значений для хранения 2^31–1 байт данных.  
  
В SQL Server 2008 добавлен элемент FILESTREAM. Это не тип данных, а определяемый на уровне столбца атрибут, позволяющий хранить данные большого размера в файловой системе, а не в базе данных.  
  
## <a name="in-this-section"></a>В этом разделе  
[Изменение данных больших значений (max) в ADO.NET](modify-large-value-max-data.md)  
Описание работы с типами данных больших значений.  
  
[Данные файлового потока](filestream-data.md)  
Описывает, как работать с данными большого объема, хранимыми в SQL Server 2008 с помощью атрибута FILESTREAM.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Типы данных SQL Server и ADO.NET](sql-server-data-types.md)
- [Операции с данными SQL Server в ADO.NET](sql-server-data-operations.md)

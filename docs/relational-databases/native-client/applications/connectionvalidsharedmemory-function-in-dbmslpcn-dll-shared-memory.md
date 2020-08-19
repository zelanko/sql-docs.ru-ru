---
description: Функция ConnectionValidSharedMemory в общей памяти dbmslpcn.dll
title: Коннектионвалидшаредмемори dbmslpcn.dll
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 6ae35826-7d75-4542-b686-5f79316b6157
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 02247866c1f83693202d649d1c05be31214b5ded
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88498937"
---
# <a name="connectionvalidsharedmemory-function-in-dbmslpcndll-shared-memory"></a>Функция ConnectionValidSharedMemory в общей памяти dbmslpcn.dll
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Функция определяет, установлена ли и активна SQL Server общая память.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
BOOL ConnectionValidSharedMemory(char * szServerName);  
```  
  
## <a name="parameters"></a>Параметры  
 *сзсервернаме*  
  
-   Тип: **char \* **  
  
-   Имя сервера SQL Server.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Тип: **bool** .  
  
 Возвращает значение 0, если недопустимо; Else возвращает ненулевое значение.  
  
  

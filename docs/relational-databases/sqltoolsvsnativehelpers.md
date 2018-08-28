---
title: SqlToolsVSNativeHelpers | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: relational-databases-misc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: d33cb556-0380-490a-9220-b74062dbd6d9
caps.latest.revision: 5
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6786e80048efc4ab4279d1e7a5fbba1aa68fbc23
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43086212"
---
# <a name="sqltoolsvsnativehelpers"></a>SqlToolsVSNativeHelpers
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Библиотека, поддерживающая функциональность SQL Server в Visual Studio.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID /*lpReserved*/)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение **True** , если точка входа библиотеки DLL инициализирована правильно; в противном случае — **False**.  
  
## <a name="see-also"></a>См. также:  
 [FrameWindowVisible](../relational-databases/sqltoolsvsnativehelpers-framewindowvisible.md)  
  
  

---
title: SqlToolsVSNativeHelpers | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: d33cb556-0380-490a-9220-b74062dbd6d9
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 992f8288018fb248b14db13b2ed1104aeecab04d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52749116"
---
# <a name="sqltoolsvsnativehelpers"></a>SqlToolsVSNativeHelpers
  Библиотека, поддерживающая функциональность SQL Server в Visual Studio.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID /*lpReserved*/)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение `True`, если точка входа библиотеки DLL инициализирована правильно; в противном случае — `False`.  
  
## <a name="see-also"></a>См. также  
 [FrameWindowVisible](sqltoolsvsnativehelpers-framewindowvisible.md)  
  
  

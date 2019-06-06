---
title: Ссылки на библиотеки ADO в приложении Visual C++ | Документация Майкрософт
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual C++ application[ADO]
- ADO, libraries
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7eb96d739a95e1b75894ab3f561f6db3c6661a21
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66699827"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Ссылки на библиотеки ADO в приложении Visual C++
Чтобы использовать последнюю версию ADO в приложении Visual C++, используйте следующую команду `#import` директивы:  
  
```cpp
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 Чтобы использовать многомерные Объекты ADO и ADOX, необходимо импортировать *msadomd.dll* или *msadox.dll*, используя приведенный выше синтаксис.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 Чтобы использовать более ранние версии ADO, замените *msado15.dll* выше с одним из следующих библиотек типов.  
  
-   *msado27.tlb*, библиотека 2.7 тип ADO  
  
-   *msado26.tlb*, библиотеку ADO 2.6 типов  
  
-   *msado25.tlb*, библиотека 2,5 тип ADO  
  
-   *msado21.tlb*, библиотека 2.1 тип ADO  
  
-   *msado20.tlb*, библиотека типов ADO 2.0

---
description: Ссылки на библиотеки ADO в приложении Visual C++
title: Ссылки на библиотеки ADO в приложении Visual C++ | Документация Майкрософт
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual C++ application[ADO]
- ADO, libraries
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
author: rothja
ms.author: jroth
ms.openlocfilehash: 7a262ef7b71b6618bdfc4ae50cec2eec3fca4a41
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88978485"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Ссылки на библиотеки ADO в приложении Visual C++
Чтобы использовать последнюю версию ADO в Visual C++ приложении, используйте следующую `#import` директиву:  
  
```cpp
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 Чтобы использовать объекты данных ActiveX (MD) или ADOX, необходимо импортировать *msadomd.dll* или *msadox.dll*с помощью приведенного выше синтаксиса.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 Чтобы использовать более раннюю версию ADO, замените *msado15.dll* выше на одну из следующих библиотек типов.  
  
-   *msado27. tlb*, Библиотека типов ADO 2,7  
  
-   *msado26. tlb*, Библиотека типов ADO 2,6  
  
-   *msado25. tlb*, Библиотека типов ADO 2,5  
  
-   *msado21. tlb*, Библиотека типов ADO 2,1  
  
-   *msado20. tlb*, Библиотека типов ADO 2,0

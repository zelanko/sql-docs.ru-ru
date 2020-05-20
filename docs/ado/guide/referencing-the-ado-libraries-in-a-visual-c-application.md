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
author: rothja
ms.author: jroth
ms.openlocfilehash: a790ace40aa31324ce8b22127d8f6948ae86e059
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764765"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Ссылки на библиотеки ADO в приложении Visual C++
Чтобы использовать последнюю версию ADO в Visual C++ приложении, используйте следующую `#import` директиву:  
  
```cpp
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 Чтобы использовать объекты данных ActiveX (MD) или ADOX, необходимо импортировать *мсадомд. dll* или *мсадокс. dll*с помощью приведенного выше синтаксиса.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 Чтобы использовать любую более раннюю версию ADO, замените *Msado15. dll* выше одной из следующих библиотек типов.  
  
-   *msado27. tlb*, Библиотека типов ADO 2,7  
  
-   *msado26. tlb*, Библиотека типов ADO 2,6  
  
-   *msado25. tlb*, Библиотека типов ADO 2,5  
  
-   *msado21. tlb*, Библиотека типов ADO 2,1  
  
-   *msado20. tlb*, Библиотека типов ADO 2,0

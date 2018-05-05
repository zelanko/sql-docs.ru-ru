---
title: Ссылающееся на библиотеки в приложении Visual C++ ADO | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual C++ application[ADO]
- ADO, libraries
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6da3515ceafb7540cbcb2b538c1951a9b4c0bc2b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Ссылающееся на библиотеки ADO в приложении Visual C++
Чтобы использовать последнюю версию ADO в приложении Visual C++, используйте следующую `#import` директиву:  
  
```  
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 Чтобы использовать ADO MD или ADOX, необходимо импортировать *msadomd.dll* или *msadox.dll*, с помощью синтаксиса выше.  
  
## <a name="backward-compatibility"></a>Обратная совместимость  
 Чтобы использовать все более ранние версии ADO, замените *msado15.dll* выше с одним из следующих библиотек типов.  
  
-   *msado27.tlb*, библиотека 2.7 тип ADO  
  
-   *msado26.tlb*, библиотека ADO 2.6 типов  
  
-   *msado25.tlb*, библиотека 2,5 тип ADO  
  
-   *msado21.tlb*, библиотека ADO 2.1 типов  
  
-   *msado20.tlb*, библиотека типов ADO 2.0

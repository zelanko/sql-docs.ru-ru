---
title: Ссылки на библиотеки ADO в приложении Visual C++ | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
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
manager: craigg
ms.openlocfilehash: fa07fc475d423cf4c338d40393c053d1dc30d488
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601992"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Ссылки на библиотеки ADO в приложении Visual C++
Чтобы использовать последнюю версию ADO в приложении Visual C++, используйте следующую команду `#import` директивы:  
  
```  
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

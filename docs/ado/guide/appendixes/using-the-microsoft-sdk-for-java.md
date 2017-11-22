---
title: "С помощью пакета Microsoft SDK для Java | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 02/15/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Java (Microsoft SDK for)
- Microsoft SDK for Java [ADO]
ms.assetid: 2d7cb5b5-8307-49dd-b07e-c07069bb1626
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1e176da2e8f67a61a4f38fa6867919d4c5bfbde7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="using-the-microsoft-sdk-for-java"></a>С помощью пакета Microsoft SDK для Java

> [!IMPORTANT]
> В января 2004 г. Корпорация Майкрософт прекращена поддержка Visual J ++.

Microsoft SDK для Java является пакет средств разработки для среды Microsoft Internet Explorer. Средства, сведения и примеры предназначены для разработки приложений Java и приложения на основе JDK 1.1 и Microsoft Win32 виртуальной машины (Microsoft VM). Microsoft SDK для Java не привязан к Microsoft Visual J ++. Чтобы загрузить этот пакет SDK, щелкните здесь.  
  
 Программа Jactivex.exe создает классы из библиотеки типов, но может быть вызван только в командной строке. Эта функция не интегрирована со средой разработки Visual J ++. В отличие от классов, созданные с помощью мастера библиотеки типов Java выполнить пошаговый заход классов-оболочек, созданные в пакете SDK. Это полезно для отладки, как код использует классы-оболочки ADO.  
  
 Этот механизм считывает ADO библиотеки типов и создает классы, которые можно создать в приложении. Он создает эти классы в следующем расположении: \\< каталог windows\>\Java\trustlib\msado15.  
  
 Создание приложения ADO на языке Java, с помощью пакета Microsoft SDK для Java идентична существенно, с точки зрения исходного кода с помощью мастера библиотеки типа Java. Пример кода, в разделе [ADO Java классов-оболочек](../../../ado/guide/appendixes/ado-java-class-wrappers.md). Единственная разница заключается в как создать классы-оболочки, в первую очередь, как показано в следующих шагах.  
  
### <a name="to-create-an-ado-project-with-the-microsoft-sdk-for-java"></a>Чтобы создать проект ADO с Microsoft SDK для Java  
  
1.  Выполните следующую команду. Необходимо задать путь для включения пакета SDK Microsoft для каталога Java Bin или выполните команду из этого расположения. Как правило в том же расположении, что и Visual Studio установлен пакет SDK Microsoft для Java. Это инструкция одной команды.  
  
    ```  
    \<path to DevStudio>\<path to Java SDK>\bin\JactiveX.exe /javatlb "C:\program files\common files\system\ado\msado15.dll"  
    ```  
  
2.  Выполните следующую команду для компиляции созданных классов. /G:t служит для включения создания символов отладки, чтобы можно было отслеживать в. Символы Java. Для сборки выпуска, удалите его.  
  
    ```  
    jvc /g:t c:\<windows>\Java\trustlib\msado15\*.Java  
    ```  
  
3.  Чтобы использовать эти файлы, откройте проект в Visual J ++. Из **проекта** меню, выберите **добавить в проект**. Выберите **файлы**и добавить все. JAVA файлы в каталоге trustlib\msado15 проект создан.  
  
## <a name="see-also"></a>См. также:  
 [Классы-оболочки Java для объектов ADO](../../../ado/guide/appendixes/ado-java-class-wrappers.md)   

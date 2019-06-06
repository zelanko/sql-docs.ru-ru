---
title: С помощью пакета Microsoft SDK для Java | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Java (Microsoft SDK for)
- Microsoft SDK for Java [ADO]
ms.assetid: 2d7cb5b5-8307-49dd-b07e-c07069bb1626
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 84c342150d00c399c4ab41c20d513b84f7be36db
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66701154"
---
# <a name="using-the-microsoft-sdk-for-java"></a>Использование пакета Microsoft SDK для Java

> [!IMPORTANT]
> Microsoft прекращена поддержка Visual J ++ в январе 2004 г.

Microsoft SDK для Java представляет собой набор разработчика в среде Microsoft Internet Explorer. Средства, сведения и примеры помогут вам в разработке Java-программ и приложений, на основе JDK 1.1 и Microsoft Win32 виртуальной машины (Microsoft VM). Microsoft SDK для Java не привязан к Microsoft Visual J ++. Чтобы загрузить этот пакет SDK, щелкните здесь.  
  
 Программа Jactivex.exe создает классы из библиотеки типов, но может вызываться только в командной строке. Этот компонент не интегрирован со средой разработки Visual J ++. В отличие от классов, созданных с помощью мастера библиотеки типов Java можно выполнить пошаговую отладку классы-оболочки, созданные с помощью пакета SDK. Это полезно для отладки, как код использует классы-оболочки ADO.  
  
 Этот механизм считывает ADO библиотеки типов и создает классы, которые можно создать в приложении. Он формирует эти классы в следующем расположении: \\< каталог windows\>\Java\trustlib\msado15.  
  
 Создание приложения ADO на языке Java с помощью пакета Microsoft SDK для Java идентична по сути, с точки зрения исходного кода, с помощью мастера библиотеки типа Java. Пример кода см. в разделе [классы-оболочки Java ADO](../../../ado/guide/appendixes/ado-java-class-wrappers.md). Единственное реальное различие заключается в как создавать классы-оболочки, в первую очередь, как показано в следующих шагах.  
  
### <a name="to-create-an-ado-project-with-the-microsoft-sdk-for-java"></a>Чтобы создать проект ADO с Microsoft SDK для Java  
  
1.  Выполните следующую команду в командной строке. Необходимо задать путь для включения пакета SDK Microsoft для каталога Java Bin, или выполните команду из этого расположения. Как правило в том же расположении, что Visual Studio устанавливается Microsoft SDK для Java. Это инструкция одной команды.  
  
    ```java
    \<path to DevStudio>\<path to Java SDK>\bin\JactiveX.exe /javatlb "C:\program files\common files\system\ado\msado15.dll"  
    ```  
  
2.  Выполните следующую команду для компиляции созданных классов. Параметр /g:t включает создание отладочных символов таким образом, вы можете отслеживать в. Символы Java. Удалите для сборок выпуска.  
  
    ```java
    jvc /g:t c:\<windows>\Java\trustlib\msado15\*.Java  
    ```  
  
3.  Чтобы использовать эти файлы, откройте проект в Visual J ++. Из **проекта** меню, выберите **добавить в проект**. Выберите **файлы**и добавьте все. Файлы JAVA, созданные в каталоге trustlib\msado15 в проект.  
  
## <a name="see-also"></a>См. также  
 [Классы-оболочки Java для объектов ADO](../../../ado/guide/appendixes/ado-java-class-wrappers.md)   

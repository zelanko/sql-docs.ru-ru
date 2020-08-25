---
description: Использование пакета Microsoft SDK для Java
title: Использование пакета Microsoft SDK для Java | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 302cca77222454ac6fa73c69683c641e841acdda
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806489"
---
# <a name="using-the-microsoft-sdk-for-java"></a>Использование пакета Microsoft SDK для Java

> [!IMPORTANT]
> Корпорация Майкрософт прекращена поддержка Visual J++ в январе 2004 января.

Пакет Microsoft SDK для Java — это набор разработчиков для среды Microsoft Internet Explorer. Средства, сведения и примеры, помогающие разрабатывать программы и приложения Java на основе JDK 1,1 и виртуальной машины Microsoft Win32 (Microsoft VM). Пакет Microsoft SDK для Java не привязан к Microsoft Visual J++. Чтобы скачать этот пакет SDK, щелкните здесь.  
  
 Служебная программа Jactivex.exe создает классы из библиотеки типов, но может вызываться только в командной строке. Эта функция не интегрирована с средой разработки Visual J++. В отличие от классов, созданных с помощью мастера библиотеки типов Java, можно выполнить шаг с заходом в оболочки классов, созданные пакетом SDK. Это полезно для отладки того, как в коде используются классы-оболочки ADO.  
  
 Этот механизм считывает библиотеку типов ADO и создает классы, которые можно создать в приложении. Он создает эти классы в следующем расположении: \\<каталог Windows \> \Java\trustlib\msado15.  
  
 Создание приложения ADO в Java с помощью пакета Microsoft SDK для Java является принципиально идентичным с точки зрения исходного кода с помощью мастера библиотеки типов Java. Пример кода см. в разделе [оболочки классов ADO Java](./ado-java-class-wrappers.md). Единственная реальная разница заключается в том, как создать классы-оболочки в первую очередь, как показано в следующих шагах.  
  
### <a name="to-create-an-ado-project-with-the-microsoft-sdk-for-java"></a>Создание проекта ADO с помощью пакета Microsoft SDK для Java  
  
1.  В командной строке выполните следующую команду. Необходимо задать путь для включения в каталог bin Microsoft SDK для Java или выполнить команду из этого расположения. Как правило, пакет Microsoft SDK для Java устанавливается в том же расположении, что и Visual Studio. Это единственный командный оператор.  
  
    ```java
    \<path to DevStudio>\<path to Java SDK>\bin\JactiveX.exe /javatlb "C:\program files\common files\system\ado\msado15.dll"  
    ```  
  
2.  Выполните следующую команду, чтобы скомпилировать созданные классы. Параметр/g: t включает создание отладочных символов, чтобы можно было выполнять трассировку в. Символы Java. Удалите его для сборок выпуска.  
  
    ```java
    jvc /g:t c:\<windows>\Java\trustlib\msado15\*.Java  
    ```  
  
3.  Чтобы использовать эти файлы, откройте проект в Visual J++. В меню **проект** выберите команду **Добавить в проект**. Выберите **файлы**и добавьте все. Файлы JAVA, созданные в каталоге trustlib\msado15 для вашего проекта.  
  
## <a name="see-also"></a>См. также  
 [Классы-оболочки Java для объектов ADO](./ado-java-class-wrappers.md)
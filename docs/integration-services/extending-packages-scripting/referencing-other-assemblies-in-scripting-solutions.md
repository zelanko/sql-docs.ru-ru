---
title: "Ссылки на другие сборки в сценарии решения | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script task, .NET Framework
- Script task [Integration Services], adding references
- referencing custom assemblies
- SSIS Script task, VisualBasic namespace
- assemblies [Integration Services]
- VisualBasic namespace
- Script task [Integration Services], VisualBasic namespace
- Microsoft.VisualBasic namespace
- Script task [Integration Services], .NET Framework
- .NET Framework [Integration Services]
- referencing Web services
ms.assetid: 9b655bcd-19f6-43d8-9f89-1b4d299c6380
caps.latest.revision: 68
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3deb13c7e3aeb2e974ac6e6582555a617346a298
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="referencing-other-assemblies-in-scripting-solutions"></a>Ссылки на другие сборки в решениях со сценариями
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Библиотека классов предоставляет разработчику скриптов набор мощных средств для реализации пользовательской функциональности в [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] пакеты. Задача «Скрипт» и компонент скрипта также могут использовать пользовательские управляемые сборки.  
  
> [!NOTE]  
>  Чтобы разрешить пакетам использование объектов и методов из веб-службы, используйте **Add Web Reference** команд, доступных в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] средств для приложений (VSTA). В более ранних версиях служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], чтобы использовать веб-службу, приходилось формировать класс-посредник.  
  
## <a name="using-a-managed-assembly"></a>Использование управляемой сборки  
 Для [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] могли найти управляемую сборку во время разработки, необходимо выполнить следующие действия:  
  
1.  Сохранить управляемую сборку в любой папке на компьютере.  
  
    > [!NOTE]  
    >  В более ранних версиях служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно было добавлять ссылки только на управляемые сборки, хранящиеся в папке %windir%\Microsoft.NET\Framework\vx.x.xxxxx или %ProgramFiles%\Microsoft SQL Server\100\SDK\Assemblies.  
  
2.  Добавить ссылку на управляемую сборку.  
  
     Для добавления ссылки в средствах VSTA в **добавить ссылку** диалогового **Обзор** найдите и добавьте управляемую сборку.  
  
 Чтобы службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] могли найти управляемую сборку во время выполнения, необходимо выполнить следующие шаги.  
  
1.  Подписать управляемую сборку строгим именем.  
  
2.  Установить сборку в глобальный кэш сборок на компьютере, где выполняется пакет.  
  
     Дополнительные сведения см. в разделе [построение, развертывание и отладка пользовательских объектов](../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).  
  
## <a name="using-the-microsoft-net-framework-class-library"></a>Использование библиотеки классов платформы Microsoft .NET Framework  
 Задача «Скрипт» и компонент Script могут использовать преимущества всех остальных объектов и функциональность, которую обеспечивает библиотека классов платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Например, с помощью платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] можно извлекать сведения о среде и взаимодействовать с компьютером, на котором работает пакет.  
  
 В следующем списке описываются некоторые из наиболее часто используемых классов платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
-   **System.Data** содержит архитектуру ADO.NET.  
  
-   **System.IO** предоставляет интерфейс для файловой системы и потоками.  
  
-   **System.Windows.Forms** обеспечивает создание форм.  
  
-   **System.Text.RegularExpressions** предоставляет классы для работы с регулярными выражениями.  
  
-   **System.Environment** возвращает сведения о локальном компьютере, текущем пользователе и настроек компьютера и пользователя.  
  
-   **System.Net** обеспечивает сетевые соединения.  
  
-   **Пространство имен System.DirectoryServices** обеспечивает доступ к Active Directory.  
  
-   **System.Drawing** предоставляет широкие изображения манипуляции библиотеки.  
  
-   **System.Threading** обеспечивает возможность многопоточного программирования.  
  
 Дополнительные сведения о платформе [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] см. в библиотеке MSDN.  
  
## <a name="see-also"></a>См. также:  
 [Расширение пакетов с помощью сценариев](../../integration-services/extending-packages-scripting/extending-packages-with-scripting.md)  
  
  

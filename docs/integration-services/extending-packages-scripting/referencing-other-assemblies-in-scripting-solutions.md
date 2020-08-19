---
description: Ссылки на другие сборки в решениях со сценариями
title: Ссылки на другие сборки в решениях со скриптами | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d476bd87096a68be5154cb57563f08ad982e7d3c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88425326"
---
# <a name="referencing-other-assemblies-in-scripting-solutions"></a>Ссылки на другие сборки в решениях со сценариями

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Библиотека классов платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] предоставляет разработчику скриптов набор эффективных средств для реализации пользовательской функциональности в пакетах служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Задача «Скрипт» и компонент скрипта также могут использовать пользовательские управляемые сборки.  
  
> [!NOTE]
>  Чтобы разрешить пакетам использование объектов и методов из веб-службы, используйте команду **Добавить веб-ссылку**, доступную в средствах [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для приложений (VSTA). В более ранних версиях служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], чтобы использовать веб-службу, приходилось формировать класс-посредник.  
  
## <a name="using-a-managed-assembly"></a>Использование управляемой сборки  
 Чтобы во время разработки службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] могли найти управляемую сборку, нужно сделать следующее:  
  
1.  Сохранить управляемую сборку в любой папке на компьютере.  
  
    > [!NOTE]  
    >  В более ранних версиях служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно было добавлять ссылки только на управляемые сборки, хранящиеся в папке %windir%\Microsoft.NET\Framework\vx.x.xxxxx или %ProgramFiles%\Microsoft SQL Server\100\SDK\Assemblies.  
  
2.  Добавить ссылку на управляемую сборку.  
  
     Чтобы добавить ссылку, в средствах VSTA в диалоговом окне **Добавление ссылки** на вкладке **Обзор** найдите и добавьте управляемую сборку.  
  
 Чтобы службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] могли найти управляемую сборку во время выполнения, необходимо выполнить следующие шаги.  
  
1.  Подписать управляемую сборку строгим именем.  
  
2.  Установить сборку в глобальный кэш сборок на компьютере, где выполняется пакет.  
  
     Дополнительные сведения см. в разделе [Сборка, развертывание и отладка пользовательских объектов](../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).  
  
## <a name="using-the-microsoft-net-framework-class-library"></a>Использование библиотеки классов платформы Microsoft .NET Framework  
 Задача «Скрипт» и компонент Script могут использовать преимущества всех остальных объектов и функциональность, которую обеспечивает библиотека классов платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Например, с помощью платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] можно извлекать сведения о среде и взаимодействовать с компьютером, на котором работает пакет.  
  
 В следующем списке описываются некоторые из наиболее часто используемых классов платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
-   **System.Data**: содержит архитектуру ADO.NET.  
  
-   **System.IO**: предоставляет интерфейс для файловой системы и файловых потоков.  
  
-   **System.Windows.Forms**: обеспечивает создание форм.  
  
-   **System.Text.RegularExpressions**: предоставляет классы для работы с регулярными выражениями.  
  
-   **System.Environment**: возвращает сведения о локальном компьютере, текущем пользователе, а также настройках компьютера и пользователя.  
  
-   **System.Net**: обеспечивает сетевые соединения.  
  
-   **System.DirectoryServices**: предоставляет Active Directory.  
  
-   **System.Drawing**: предоставляет обширные библиотеки для операций с изображениями.  
  
-   **System.Threading**: обеспечивает возможность многопоточного программирования.  
  
 Дополнительные сведения о платформе [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] см. в библиотеке MSDN.  
  
## <a name="see-also"></a>См. также  
 [Расширение пакетов с помощью сценариев](../../integration-services/extending-packages-scripting/extending-packages-with-scripting.md)  
  
  

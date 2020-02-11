---
title: Ссылки на другие сборки в решениях со скриптами | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a6f942e1afe40467e331519f276b360f87f9a6da
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62894738"
---
# <a name="referencing-other-assemblies-in-scripting-solutions"></a>Ссылки на другие сборки в решениях со сценариями
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Библиотека классов предоставляет разработчику скриптов мощный набор средств для реализации пользовательских функций в [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] пакетах. Задача «Скрипт» и компонент скрипта также могут использовать пользовательские управляемые сборки.  
  
> [!NOTE]  
>  Чтобы разрешить пакетам использовать объекты и методы из веб-службы, используйте команду **Добавить веб-ссылку** , доступную в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] статье средства для приложений (VSTA). В более ранних версиях служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], чтобы использовать веб-службу, приходилось формировать класс-посредник.  
  
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
  
     Дополнительные сведения см. в разделе [Сборка, развертывание и отладка пользовательских объектов](../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).  
  
## <a name="using-the-microsoft-net-framework-class-library"></a>Использование библиотеки классов платформы Microsoft .NET Framework  
 Задача «Скрипт» и компонент Script могут использовать преимущества всех остальных объектов и функциональность, которую обеспечивает библиотека классов платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Например, с помощью платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] можно извлекать сведения о среде и взаимодействовать с компьютером, на котором работает пакет.  
  
 В следующем списке описываются некоторые из наиболее часто используемых классов платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
-   `System.Data`Содержит архитектуру ADO.NET.  
  
-   `System.IO`Предоставляет интерфейс для файловой системы и потоков.  
  
-   `System.Windows.Forms`Обеспечивает создание форм.  
  
-   `System.Text.RegularExpressions`Предоставляет классы для работы с регулярными выражениями.  
  
-   `System.Environment`Возвращает сведения о локальном компьютере, текущем пользователе, а также о параметрах компьютера и пользователя.  
  
-   `System.Net`Обеспечивает сетевую связь.  
  
-   `System.DirectoryServices`Предоставляет Active Directory.  
  
-   `System.Drawing`Предоставляет обширные библиотеки управления образами.  
  
-   `System.Threading`Включает многопоточное программирование.  
  
 Дополнительные сведения о платформе [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] см. в библиотеке MSDN.  
  
![Значок Integration Services (маленький)](../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Расширение пакетов с помощью сценариев](extending-packages-with-scripting.md)  
  
  

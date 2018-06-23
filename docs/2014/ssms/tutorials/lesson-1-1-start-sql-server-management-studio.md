---
title: Запуск SQL Server Management Studio | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
caps.latest.revision: 43
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2f928645fb89757b2284628d0400847cf5f3a1f2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087978"
---
# <a name="start-sql-server-management-studio"></a>Запуск среды SQL Server Management Studio
  В начале этого учебника кратко рассмотрим среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="opening-sql-server-management-studio"></a>Открытие среды SQL Server Management Studio  
  
#### <a name="to-open-sql-server-management-studio"></a>Открытие среды SQL Server Management Studio  
  
1.  На **запустить** последовательно выберите пункты **все программы**, пункты [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], а затем нажмите кнопку **SQL Server Management Studio**.  
  
    > [!NOTE]  
    >  Среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] не устанавливается по умолчанию. Если среда [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] недоступна, установите ее с помощью программы установки. Среда [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] не входит в состав [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express доступна для бесплатной загрузки из [центра загрузки Майкрософт](http://go.microsoft.com/fwlink/?LinkID=37075&clcid=0x409), но имеет другой пользовательский интерфейс, отличный от описываемого в этом учебнике.  
  
2.  В диалоговом окне **Соединение с сервером** подтвердите заданные по умолчанию параметры, а затем нажмите кнопку **Подключиться**. Чтобы подключиться, **имя сервера** поле должно содержать имя компьютера, где [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлен. Если [!INCLUDE[ssDE](../../includes/ssde-md.md)] является именованным экземпляром, **имя сервера** поле должно также содержать имя экземпляра в формате \< *имя_компьютера* > \\ < *имя_экземпляра*>.  
  
## <a name="management-studio-components"></a>Компоненты среды Management Studio  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] представляет данные в виде окон, выделенных для отдельных типов данных. Сведения о базе данных отображаются в обозревателе объектов и окнах документов.  
  
-   Обозреватель объектов является представлением в виде дерева, в котором отображаются все объекты базы данных на сервере. Он может содержать базы данных компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]и служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Обозреватель объектов включает сведения по всем серверам, к которым он подключен. При открытии среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]пользователю предлагается применить при подключении обозревателя объектов параметры, которые использовались в прошлый раз. Чтобы подключиться к любому из серверов, следует дважды щелкнуть его в компоненте «Зарегистрированные серверы», однако регистрировать его не обязательно.  
  
-   Окно документов представляет собой наиболее крупную часть среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. В окнах документов могут размещаться редакторы запросов и окна браузера. По умолчанию отображается страница «Сводка», подключенная к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] на текущем компьютере.  
  
## <a name="showing-additional-windows"></a>Отображение дополнительных окон  
  
#### <a name="to-show-the-registered-servers-window"></a>Отображение окна «Зарегистрированные серверы»  
  
1.  В меню **Вид** выберите пункт **Зарегистрированные серверы**.  
  
     Сверху от обозревателя объектов появится окно «Зарегистрированные серверы». В списке зарегистрированных серверов указаны серверы, работу которых приходится часто регулировать. В этом списке можно добавлять и удалять серверы. В этом списке указываются только экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере, где запущена среда [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  Если ваш сервер не отображается, в списке зарегистрированных серверов щелкните правой кнопкой мыши **СУБД**, а затем нажмите кнопку **обновить регистрацию локального сервера**.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Подключение к зарегистрированным серверам и к обозревателю объектов](../object/object-explorer.md)  
  
  
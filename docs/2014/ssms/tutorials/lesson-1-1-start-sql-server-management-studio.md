---
title: Запуск SQL Server Management Studio | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bd7fed6fff4ddd55ef56e4c5b342c56b6c2f462f
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632795"
---
# <a name="start-sql-server-management-studio"></a>Запуск среды SQL Server Management Studio
  В начале этого учебника кратко рассмотрим среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="opening-sql-server-management-studio"></a>Открытие среды SQL Server Management Studio  
  
#### <a name="to-open-sql-server-management-studio"></a>Открытие среды SQL Server Management Studio  
  
1.  В меню **Пуск** укажите пункт **Все программы**, укажите пункт [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]и выберите команду **Среда SQL Server Management Studio**.  
  
    > [!NOTE]  
    >  Среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] не устанавливается по умолчанию. Если среда [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] недоступна, установите ее с помощью программы установки. Среда [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] не входит в состав [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express можно скачать бесплатно из [центра загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=7593), но имеет другой пользовательский интерфейс, чем описано в этом руководстве.  
  
2.  В диалоговом окне **Соединение с сервером** подтвердите заданные по умолчанию параметры, а затем нажмите кнопку **Подключиться**. Для подключения поле **имя сервера** должно содержать имя компьютера, на котором установлен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если [!INCLUDE[ssDE](../../includes/ssde-md.md)] является именованным экземпляром, в поле **имя сервера** также должно содержаться имя экземпляра в формате \<*computer_name*> *\\<,* instance_name >.  
  
## <a name="management-studio-components"></a>Компоненты среды Management Studio  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] представляет данные в виде окон, выделенных для отдельных типов данных. Сведения о базе данных отображаются в обозревателе объектов и окнах документов.  
  
-   Обозреватель объектов является представлением в виде дерева, в котором отображаются все объекты базы данных на сервере. Он может содержать базы данных компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]и служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Обозреватель объектов включает сведения по всем серверам, к которым он подключен. При открытии среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]пользователю предлагается применить при подключении обозревателя объектов параметры, которые использовались в прошлый раз. Чтобы подключиться к любому из серверов, следует дважды щелкнуть его в компоненте «Зарегистрированные серверы», однако регистрировать его не обязательно.  
  
-   Окно документов представляет собой наиболее крупную часть среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. В окнах документов могут размещаться редакторы запросов и окна браузера. По умолчанию отображается страница «Сводка», подключенная к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] на текущем компьютере.  
  
## <a name="showing-additional-windows"></a>Отображение дополнительных окон  
  
#### <a name="to-show-the-registered-servers-window"></a>Отображение окна «Зарегистрированные серверы»  
  
1.  В меню **Вид** выберите пункт **Зарегистрированные серверы**.  
  
     Сверху от обозревателя объектов появится окно «Зарегистрированные серверы». В списке зарегистрированных серверов указаны серверы, работу которых приходится часто регулировать. В этом списке можно добавлять и удалять серверы. В этом списке указываются только экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере, где запущена среда [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  Если сервер не отображается, в окне "зарегистрированные серверы" щелкните правой кнопкой мыши **ядро СУБД**, а затем выберите **Обновить регистрацию локального сервера**.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Подключение к зарегистрированным серверам и к обозревателю объектов](../object/object-explorer.md)  
  
  

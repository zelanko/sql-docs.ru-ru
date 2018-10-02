---
title: Администрирование серверов при помощи среды SQL Server Management Studio | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b06376518361b0ab33d227e11a06654bfc3618f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47657408"
---
# <a name="administer-servers-with-sql-server-management-studio"></a>Администрирование серверов при помощи среды SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[msCoName](../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] является полнофункциональным интегрированным административным клиентом, разработанным для решения задач администратора сервера [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и базы данных SQL Azure. В среде [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]задачи администрирования выполняются при помощи обозревателя объектов, который позволяет подключиться к любому серверу семейства [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и просматривать его содержимое при помощи графических средств. Сервер может быть экземпляром компонента [!INCLUDE[ssDE](../includes/ssde_md.md)], [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] или базы данных SQL Azure.  
  
В число средств среды [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] входят зарегистрированные серверы, обозреватель объектов, обозреватель решений, обозреватель шаблонов, страница сводки и окно документа. Чтобы отобразить средство, в меню **Вид** выберите его название. Для отображения редактора запросов нажмите кнопку **Создать запрос** на панели инструментов.  
  
> [!IMPORTANT]  
> По умолчанию сетевой трафик между [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] и [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] не шифруется. Не работайте в среде [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] с конфиденциальными данными (включая пароли), не установив шифруемого соединения. Дополнительные сведения см. в разделе [Практическое руководство. Включение шифрования соединений в ядре СУБД (диспетчер конфигурации SQL Server)](http://msdn.microsoft.com/e1e55519-97ec-4404-81ef-881da3b42006).  
  
Используйте среду [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] для выполнения следующих действий:  
  
-   регистрации серверов;  
  
-   соединения с экземпляром [!INCLUDE[ssDE](../includes/ssde_md.md)], SSAS, [!INCLUDE[ssRS](../includes/ssrs.md)], [!INCLUDE[ssIS](../includes/ssis_md.md)]  или базы данных SQL Azure;  
  
-   настройки свойств сервера;  
  
-   управления объектами базы данных и службами SSAS, такими как кубы, измерения и сборки;  
  
-   создания таких объектов, как базы данных, таблицы, кубы, пользователи базы данных и имена входа;  
  
-   управления файлами и группами файлов;  
  
-   присоединения или отсоединения баз данных;  
  
-   запуска средств для работы со сценариями;  
  
-   управления безопасностью;  
  
-   просмотра системных журналов;  
  
-   контроля текущей активности;  
  
-   настройки репликации;  
  
-   управления полнотекстовыми индексами.  
  
Для запуска и остановки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] следует использовать диспетчер конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
[Использование среды SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
[Практическое руководство. Просмотр свойств сервера (среда SQL Server Management Studio)](http://msdn.microsoft.com/55f3ac04-5626-4ad2-96bd-a1f1b079659d)  
  

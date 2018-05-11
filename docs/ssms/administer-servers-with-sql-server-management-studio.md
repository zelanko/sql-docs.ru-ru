---
title: Администрирование серверов при помощи среды SQL Server Management Studio | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 024175506b041ae9c62585dbdcc05da4b84bea02
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="administer-servers-with-sql-server-management-studio"></a>Администрирование серверов при помощи среды SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[msCoName](../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] является полнофункциональным интегрированным административным клиентом, разработанным для решения задач администратора сервера [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] и базы данных SQL Azure. В среде [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)]задачи администрирования выполняются при помощи обозревателя объектов, который позволяет подключиться к любому серверу семейства [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] и просматривать его содержимое при помощи графических средств. Сервер может быть экземпляром компонента [!INCLUDE[ssDE](../includes/ssde_md.md)], [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion_md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion_md.md)] или базы данных SQL Azure.  
  
В число средств среды [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] входят зарегистрированные серверы, обозреватель объектов, обозреватель решений, обозреватель шаблонов, страница сводки и окно документа. Чтобы отобразить средство, в меню **Вид** выберите его название. Для отображения редактора запросов нажмите кнопку **Создать запрос** на панели инструментов.  
  
> [!IMPORTANT]  
> По умолчанию сетевой трафик между [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] и [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] не шифруется. Не работайте в среде [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] с конфиденциальными данными (включая пароли), не установив шифруемого соединения. Дополнительные сведения см. в разделе [Практическое руководство. Включение шифрования соединений в ядре СУБД (диспетчер конфигурации SQL Server)](http://msdn.microsoft.com/en-us/e1e55519-97ec-4404-81ef-881da3b42006).  
  
Используйте среду [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] для выполнения следующих действий:  
  
-   регистрации серверов;  
  
-   соединения с экземпляром [!INCLUDE[ssDE](../includes/ssde_md.md)], [!INCLUDE[ssAS](../includes/ssas_md.md)], [!INCLUDE[ssRS](../includes/ssrs_md.md)],  [!INCLUDE[ssIS](../includes/ssis_md.md)] или базы данных SQL Azure;  
  
-   настройки свойств сервера;  
  
-   управления объектами базы данных и службами [!INCLUDE[ssAS](../includes/ssas_md.md)] , такими как кубы, измерения и сборки;  
  
-   создания таких объектов, как базы данных, таблицы, кубы, пользователи базы данных и имена входа;  
  
-   управления файлами и группами файлов;  
  
-   присоединения или отсоединения баз данных;  
  
-   запуска средств для работы со сценариями;  
  
-   управления безопасностью;  
  
-   просмотра системных журналов;  
  
-   контроля текущей активности;  
  
-   настройки репликации;  
  
-   управления полнотекстовыми индексами.  
  
Для запуска и остановки [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] или агента [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] следует использовать диспетчер конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] .  
  
## <a name="see-also"></a>См. также:  
[Использование среды SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
[Практическое руководство. Просмотр свойств сервера (среда SQL Server Management Studio)](http://msdn.microsoft.com/en-us/55f3ac04-5626-4ad2-96bd-a1f1b079659d)  
  

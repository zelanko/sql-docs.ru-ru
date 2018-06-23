---
title: Сообщения о состоянии сервера (основной режим служб SSRS) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.rsconfigtool.serverstatus.F1
ms.assetid: 2f63ad1c-1bc2-449d-b451-fb39a0060838
caps.latest.revision: 14
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 914b5ffb0d7cbdfa2368966e110fe4d7ecf278ff
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098340"
---
# <a name="report-server-status-ssrs-native-mode"></a>Состояние сервера отчетов (службы Reporting Services в собственном режиме)
  Эта страница позволяет просмотреть сведения о состоянии экземпляра сервера отчетов, с которым в настоящий момент установлено соединение. Данная страница является начальной для настройки сервера отчетов. Доступны также дополнительные страницы, предназначенные для настройки URL-адресов, учетной записи службы, базы данных сервера отчетов, доставки электронной почты сервера отчетов, параметров масштабного развертывания и ключей шифрования.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме.  
  
 Чтобы открыть эту страницу, запустите диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и подключитесь к экземпляру сервера отчетов. Дополнительные сведения см. в разделе [диспетчер конфигурации служб Reporting Services &#40;del&#41;](/sql/2014/sql-server/install/reporting-services-configuration-manager-native-mode).  
  
> [!TIP]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool.exe) устанавливается с уровнем прав доступа «highestAvailable». Это поведение предусмотрено намеренно. Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] требует подключения к API-интерфейсам [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI. Для некоторых средств [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI требуется более высокий уровень прав администратора.  
  
 Если при подключении к серверу отчетов все ссылки страницы затенены, убедитесь, что сервер отчетов запущен. Параметр **Состояние службы отчетов:** должен иметь значение "Работает". Для определения состояния сервера также можно использовать консольное приложение «Службы» в «Администрировании».  
  
## <a name="options"></a>Параметры  
 **Экземпляр SQL Server**  
 Отображает сведения об экземпляре сервера отчетов, с которым имеется соединение в текущий момент. Имена экземпляров сервера отчетов основаны на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] именованных экземпляров. Имя экземпляра по умолчанию — «MSSQLSERVER», а имя именованного экземпляра — значение, указанное во время установки. Дополнительные сведения об экземплярах см. в разделе [работать с несколькими версиями и экземплярами SQL Server](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации.  
  
> [!NOTE]  
>  В выпуске SQL Server Express with Advanced Services экземпляром по умолчанию является SQLExpress.  
  
 **Идентификатор экземпляра**  
 Соответствует папке файловой системы, в которой хранятся программные файлы подключенного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **Идентификатор экземпляра** присваивается программой установки в формате *компонент*. *экземпляр*, где *компонент* является значением, указывающим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компонента и *экземпляр* — именем экземпляра. Имя экземпляра по умолчанию — MSSQLSERVER. Например, если устанавливаются экземпляры по умолчанию [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ниже приведены компоненты, именами папок:  
  
-   MSSQL12.MSSQLSERVER  
  
-   MSAS12.MSSQLSERVER  
  
-   MSRS12.MSSQLSERVER  
  
 Если устанавливается второй экземпляр компонента, который уже установлены, таких как [!INCLUDE[ssDE](../../includes/ssde-md.md)], и имя экземпляра Contoso, **идентификатор экземпляра** — MSSQL12. Contoso.  
  
 **Выпуск**  
 Отображает сведения о выпуске. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](http://go.microsoft.com/fwlink/?linkid=232473).  
  
 **Номер версии продукта**  
 Отображает версию [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , которые установлены.  
  
 **База данных сервера отчетов**  
 Отображает имя базы данных сервера отчетов, в которой хранятся данные о приложении для текущего экземпляра сервера отчетов.  
  
 **Режим сервера отчетов**  
 В этом поле всегда должно отображаться значение **Собственный**. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration manager поддерживает только собственный режим сервера отчетов. Если отображается значение **Режим интеграции с SharePoint**, это может указывать на то, что развертывание собственного режима настроено неправильно, в связи с чем требуется подключиться к каталогу отчетов, работающему в собственном режиме. На странице **База данных** диспетчера конфигурации измените базу данных и либо создайте новую базу данных, либо подключитесь к существующему каталогу баз данных сервера отчетов, работающего в собственном режиме.  
  
 **Состояние сервера**  
 Указывает, запущена ли служба сервера отчетов.  
  
 **Запуск**  
 Запускает службу сервера отчетов. Перезапуск службы необходим после некоторых изменений конфигурации (например, при перенастройке сервера отчетов после изменения имени компьютера). При изменении конфигурации резервирования URL-адресов служба перезапустится автоматически. Кроме того, перезапуск необходим для того, чтобы применить изменения.  
  
 **Остановить**  
 Останавливает службу сервера отчетов. Остановка службы приводит к прекращению работы сервера отчетов. Дополнительные сведения см. в разделе [запуска и остановки службы сервера отчетов](../../reporting-services/report-server/start-and-stop-the-report-server-service.md) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации.  
  
## <a name="see-also"></a>См. также  
 [Разделы справки F1 по диспетчеру конфигурации служб Reporting Services &#40;собственный режим служб SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Диспетчер конфигурации служб Reporting Services &#40;del&#41;](/sql/2014/sql-server/install/reporting-services-configuration-manager-native-mode)   
 [Инициализация сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)  
  
  

---
title: Задание свойств службы Integration Services | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Integration Services service, configuring
- Integration Services service, properties
ms.assetid: 3a8ad546-0f58-4b31-ab56-58d6313b1098
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 70ff196fbaba6f7b104e242d7c4f74afc48f190a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101999"
---
# <a name="set-the-properties-of-the-integration-services-service"></a>задать свойства службы Integration Services
    
> [!IMPORTANT]  
>  В данном разделе описывается компонент [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] — служба Windows для управления пакетами служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] поддерживает эту службу для обеспечения обратной совместимости с более ранними версиями служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Начиная с [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], на сервере служб Integration Services можно управлять пакетами.  
  
 Служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] управляет и отслеживает пакеты в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. После первой установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]запускается служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , а тип запуска для нее устанавливается на автоматический.  
  
 После установки службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] можно задавать свойства службы, используя диспетчер конфигурации SQL Server или оснастку Services консоли MMC.  
  
 Чтобы настроить другие важные функции службы, включая местоположения, в которых осуществляется хранение и управление пакетами, необходимо внести изменения в файл конфигурации службы. Дополнительные сведения см. в разделе [Настройка служб Integration Services (SSIS)](service/integration-services-service-ssis-service.md).  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-sql-server-configuration-manager"></a>Определение свойств службы Integration Services с использованием диспетчера конфигурации SQL Server  
  
1.  В меню **Пуск** укажите **Все программы**, **Microsoft SQL Server**, **Средства настройки**и выберите пункт **Диспетчер конфигурации SQL Server**.  
  
2.  В оснастке **Диспетчер конфигурации SQL Server** в списке служб найдите **Службы SQL Server Integration Services** , щелкните правой кнопкой мыши **Службы SQL Server Integration Services**и выберите **Свойства**.  
  
3.  В диалоговом окне **Свойства служб SQL Server Integration Services** можно выполнить следующие действия.  
  
    -   Перейдите на вкладку **Вход** , чтобы просмотреть учетные данные, такие как имя учетной записи.  
  
    -   Перейдите на вкладку **Служба** , чтобы просмотреть сведения о службе, такие как имя главного компьютера, и указать режим запуска службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
        > [!NOTE]  
        >  На вкладке **Дополнительно** сведений о службе [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] не содержится.  
  
4.  Нажмите кнопку **ОК**.  
  
5.  Чтобы закрыть оснастку **Диспетчер конфигурации SQL Server** , в меню **Файл** выберите пункт **Выход** .  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-services"></a>Определение свойств службы Integration Services с использованием оснастки Services  
  
1.  При использовании классического вида **панели управления**щелкните **Администрирование**; если используется вид по категориям, щелкните **Производительность и обслуживание** , а затем **Администрирование**.  
  
2.  Щелкните **Службы**.  
  
3.  В оснастке **Службы** в списке служб найдите **SQL Server Integration Services** , щелкните правой кнопкой мыши **SQL Server Integration Services**и выберите пункт **Свойства**.  
  
4.  В диалоговом окне **Свойства служб SQL Server Integration Services** можно выполнить следующие действия.  
  
    -   Перейдите на вкладку **Общие** . Чтобы включить службу, выберите ручной или автоматический запуск. Чтобы выключить службу, выберите «Отключено» в поле **Тип запуска** . Выбор варианта «Отключено» не останавливает службу, если она работает в данный момент.  
  
         Если служба уже включена, можно нажать кнопку **Стоп** для остановки службы или **Пуск** для запуска службы.  
  
    -   Перейдите на вкладку **Вход** , чтобы просмотреть или изменить учетные данные.  
  
    -   Перейдите на вкладку **Восстановление** для просмотра реакции компьютера по умолчанию на ошибку в работе службы. Эти параметры можно изменять в соответствии с требованиями среды.  
  
    -   Перейдите на вкладку **Зависимости** для просмотра перечня зависимых служб. У служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] нет зависимостей.  
  
5.  Нажмите кнопку **ОК**.  
  
6.  При необходимости, если тип запуска ручной или автоматический, можно щелкнуть правой кнопкой мыши службы **SQL Server Integration Services** и выбрать пункт **Пуск, Стоп или Перезапустить**.  
  
7.  Чтобы закрыть оснастку **Службы** , в меню **Файл** выберите пункт **Выход** .  
  
## <a name="see-also"></a>См. также  
 [Управление службой Integration Services](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  
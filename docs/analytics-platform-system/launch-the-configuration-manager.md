---
title: "Запустите Диспетчер конфигураций (система платформы аналитики)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b914ba9a-e4ec-4750-934a-c447fc8909e3
caps.latest.revision: "22"
ms.openlocfilehash: 98ae90d198b4a1b68e1b72305721611a8efa30ff
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="launch-the-configuration-manager"></a>Запустите диспетчер конфигурации
Этот раздел содержит инструкции по запуску **Configuration Manager** для устройства Analytics Platform System.  
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="prerequisites"></a>Предварительные требования  
Система платформы аналитики**Configuration Manager** можно выполнить только администратор домена приложения. Для запуска этого средства требуется пароль для администратор домена приложения. Для создания дополнительных администраторов APS см [создать администратора домена APS & #40; APS & #41; ](create-an-aps-domain-administrator-aps.md).  
  
## <a name="Accessing"></a>Запустите средство диспетчера конфигурации  
Чтобы запустить диспетчер конфигурации, использование удаленного рабочего стола для подключения к узлу управления PDW (***PDW_region*-CTL01**) узла, а вход в качестве *appliance_domain* **\Administrator**. При запуске **Configuration Manager** программы, используйте **Запуск от имени администратора** параметр, чтобы убедиться, что используются учетные данные администратора.  
  
#### <a name="to-launch-from-a-browser-window"></a>Чтобы запустить из окна браузера  
  
1.  Откройте браузер и перейдите в каталог `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
2.  Щелкните правой кнопкой мыши `dwconfig.exe` и нажмите кнопку **Запуск от имени администратора**.  
  
#### <a name="to-launch-from-a-command-prompt"></a>Для запуска из командной строки  
  
1.  На рабочем столе откройте **запустить** меню, нажмите кнопку **программы**, нажмите кнопку **стандартные**, щелкните правой кнопкой мыши **командной строки** и нажмите кнопку ** Запуск от имени администратора**.  
  
2.  В командной строке введите следующую команду, чтобы изменить каталоги: `cd /d "C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100"`.  
  
3.  В командной строке введите `dwconfig.exe`.  
  
После **Configuration Manager** будет запущена, вы увидите все доступные функции, перечисленные в левой области. В оставшейся части этого раздела рассматривается выполнение каждого действия, доступные в программе.  
  
Чтобы закрыть и выйти из **Configuration Manager**, нажмите кнопку **выхода** в правом нижнем углу любого экрана.  
  
![SQL_Server_PDW_DWConfig_ApplTop](./media/launch-the-configuration-manager/SQL_Server_PDW_DWConfig_ApplTop.png "SQL_Server_PDW_DWConfig_ApplTop")  
  
## <a name="see-also"></a>См. также:  
[Мониторинг устройства с помощью консоли администрирования & #40; Система платформы аналитики & #41;](monitor-the-appliance-by-using-the-admin-console.md)  
  

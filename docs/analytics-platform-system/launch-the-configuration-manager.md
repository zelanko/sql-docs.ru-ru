---
title: Запустите диспетчер конфигурации - Analytics Platform System | Документация Майкрософт
description: Инструкции по запуску средство Configuration Manager для Analytics Platform System appliance.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 7aef9ada4a93605460cf2759dbe9deeddfc9e0d9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960729"
---
# <a name="launch-the-configuration-manager-in-analytics-platform-system"></a>Запустить диспетчер конфигурации служб в Analytics Platform System
Этот раздел содержит инструкции по запуску **Configuration Manager** для Analytics Platform System appliance.  
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="prerequisites"></a>предварительные требования  
Система платформы аналитики**Configuration Manager** может выполняться только администратором домена устройства. Чтобы запустить это средство, потребуется пароль администратор домена приложения. Чтобы создать дополнительных администраторов APS, см. в разделе [создайте учетную запись администратора домена APS &#40;APS&#41;](create-an-aps-domain-administrator-aps.md).  
  
## <a name="Accessing"></a>Запустить средство Configuration Manager  
Чтобы запустить Configuration Manager, использование удаленного рабочего стола для подключения к узлу управления PDW ( **_PDW_region_-CTL01**) узла и выполните вход как _appliance_domain_ **\Administrator**. При запуске **Configuration Manager** программы, используйте **Запуск от имени администратора** параметр, чтобы убедиться, что используются учетные данные администратора.  
  
#### <a name="to-launch-from-a-browser-window"></a>Чтобы запустить из окна браузера  
  
1.  Откройте браузер и перейдите в каталог `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
2.  Щелкните правой кнопкой мыши `dwconfig.exe` и нажмите кнопку **Запуск от имени администратора**.  
  
#### <a name="to-launch-from-a-command-prompt"></a>Для запуска из командной строки  
  
1.  На рабочем столе откройте **запустить** меню, щелкните **программы**, нажмите кнопку **стандартные**, щелкните правой кнопкой мыши **командной** и нажмите кнопку  **Запуск от имени администратора**.  
  
2.  В командной строке введите следующую команду, чтобы изменить каталоги: `cd /d "C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100"`.  
  
3.  В командной строке введите `dwconfig.exe`.  
  
После **Configuration Manager** является работу, вы увидите все доступные функции, перечисленные в левой области. В оставшейся части этого раздела описывается выполнение каждого действия, доступные в средстве.  
  
Чтобы закрыть и выйти из **Configuration Manager**, нажмите кнопку **выйти из** в правом нижнем углу любого экрана.  
  
![SQL_Server_PDW_DWConfig_ApplTop](./media/launch-the-configuration-manager/SQL_Server_PDW_DWConfig_ApplTop.png "SQL_Server_PDW_DWConfig_ApplTop")  
  
## <a name="see-also"></a>См. также  
[Мониторинг устройства с помощью консоли администрирования &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  

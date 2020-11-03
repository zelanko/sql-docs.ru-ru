---
title: Запустить Configuration Manager
description: Инструкции по запуску средства Configuration Manager для устройства аналитики платформы.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: be69331ec9f9daa091035d6ef21142c4f40d6a84
ms.sourcegitcommit: 442fbe1655d629ecef273b02fae1beb2455a762e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93235171"
---
# <a name="launch-the-configuration-manager-in-analytics-platform-system"></a>Запуск Configuration Manager в системе аналитики платформы
В этом разделе приводятся инструкции по запуску **Configuration Manager** для устройства Analytics Platform System.  
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="prerequisites"></a>Предварительные требования  
Системная платформа аналитики **Configuration Manager** может запускаться только администратором домена устройства. Для запуска этого средства необходим пароль администратора домена устройства. Сведения о создании дополнительных администраторов APS см. в статье [Создание администратора домена aps &#40;тд&#41;](create-an-aps-domain-administrator-aps.md).  
  
## <a name="launch-the-configuration-manager-tool"></a><a name="Accessing"></a>Запуск средства Configuration Manager  
Чтобы запустить Configuration Manager, используйте удаленный рабочий стол для подключения к узлу элемента управления PDW ( **_PDW_region_ -CTL01** ) и войдите в систему как _appliance_domain_**\ администратор** . При запуске программы **Configuration Manager** используйте команду **Запуск от имени администратора** , чтобы убедиться в том, что учетные данные администратора используются.  
  
#### <a name="to-launch-from-a-browser-window"></a>Запуск из окна браузера  
  
1.  Откройте браузер и перейдите в каталог `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100` .  
  
2.  Правой кнопкой мыши щелкните `dwconfig.exe` и выберите пункт **Запуск от имени администратора** .  
  
#### <a name="to-launch-from-a-command-prompt"></a>Запуск из командной строки  
  
1.  На рабочем столе откройте меню **Пуск** , выберите пункт **программы** , затем **стандартные** , щелкните правой кнопкой мыши пункт **Командная строка** и выберите команду **Запуск от имени администратора** .  
  
2.  В командной строке введите следующую команду, чтобы изменить каталоги: `cd /d "C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100"` .  
  
3.  В командной строке введите `dwconfig.exe`.  
  
После запуска **Configuration Manager** вы увидите все доступные функции, перечисленные в левой области. Оставшаяся часть этого раздела посвящена выполнению каждого действия, доступного в средстве.  
  
Чтобы закрыть и выйти **Configuration Manager** , нажмите кнопку **выход** в правом нижнем углу любого экрана.  
  
![Снимок экрана: диалоговое окно Microsoft Analytics Platform System Configuration Manager, в котором отображается топология устройства.](./media/launch-the-configuration-manager/SQL_Server_PDW_DWConfig_ApplTop.png "SQL_Server_PDW_DWConfig_ApplTop")  
  
## <a name="see-also"></a>См. также:  
[Мониторинг устройства с помощью консоли администрирования &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  

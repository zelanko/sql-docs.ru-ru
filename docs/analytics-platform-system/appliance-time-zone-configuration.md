---
title: Настройка часового пояса
description: На странице «часовой пояс» можно задать часовой пояс для всех узлов на устройстве системы аналитики (ТД).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 1da16790d011a628bc2536de051eb1181f06b8cf
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401396"
---
# <a name="appliance-time-zone-configuration---analytics-platform-system"></a>Настройка часового пояса устройства — аналитика система платформы
На странице « **Часовой пояс** » можно задать часовой пояс для всех узлов на устройстве системы АНАЛИТИКИ (ТД).  
  
## <a name="to-set-the-time-zone"></a>Задание часового пояса  
  
1.  Запустите Configuration Manager. Дополнительные сведения см. [в статье запуск Configuration Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Останавливает службы устройства с помощью страницы **состояние служб** в Configuration Manager. Инструкции см. в разделе [состояние служб PDW &#40;Analytics Platform System&#41;](pdw-services-status.md) .  
  
3.  В левой области Configuration Manager щелкните **Часовой пояс**. Выберите нужный часовой пояс в раскрывающемся меню **Часовой пояс** . В зависимости от расположения можно также выбрать флажок **автоматически настроить часы для перехода на летнее время**.  
  
4.  Нажмите кнопку **Применить** , чтобы сохранить изменения.  
  
5.  Перезапустите службы устройств с помощью страницы **состояние служб** в Configuration Manager. Если вы планируете изменить привилегии, это можно сделать перед перезапуском устройства.  
  
![Время устройств DWConfig](./media/appliance-time-zone-configuration/SQL_Server_PDW_DWConfig_ApplTopTime.png "SQL_Server_PDW_DWConfig_ApplTopTime")  
  
## <a name="see-also"></a>См. также  
[Запустите систему Configuration Manager &#40;Analytics Platform&#41;](launch-the-configuration-manager.md)  
  

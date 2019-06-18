---
title: Настройте часовой пояс - Analytics Platform System | Документация Майкрософт
description: На странице часовой пояс позволяет задать часовой пояс для всех узлов на устройстве Analytics Platform System (APS).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 6a17ef4e77f9703a285f1e232077582e4441f293
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63276006"
---
# <a name="appliance-time-zone-configuration---analytics-platform-system"></a>Конфигурация часового пояса устройства - Analytics Platform System
**Часовой пояс** страница позволяет задать часовой пояс для всех узлов на устройстве Analytics Platform System (APS).  
  
## <a name="to-set-the-time-zone"></a>Чтобы задать часовой пояс  
  
1.  Запустите диспетчер конфигурации. Дополнительные сведения см. в разделе [запустить диспетчер конфигурации служб &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Остановка служб устройства с помощью **состояние служб** страницы в Configuration Manager. См. в разделе [состояние служб PDW &#40;Analytics Platform System&#41; ](pdw-services-status.md) инструкции.  
  
3.  В левой области Configuration Manager щелкните **часовой пояс**. Выберите нужный часовой пояс из **часовой пояс** раскрывающееся меню. В зависимости от того, в расположении, вы также можете установите флажок рядом с полем **автоматически корректировались перехода на летнее время**.  
  
4.  Нажмите кнопку **применить** для сохранения изменений.  
  
5.  Перезапустите службы устройство с помощью **состояние служб** страницы в Configuration Manager. Если вы планируете также изменили разрешения, это можно сделать перед перезапуском устройства.  
  
![Время устройств DWConfig](./media/appliance-time-zone-configuration/SQL_Server_PDW_DWConfig_ApplTopTime.png "SQL_Server_PDW_DWConfig_ApplTopTime")  
  
## <a name="see-also"></a>См. также  
[Запустить диспетчер конфигурации служб &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)  
  

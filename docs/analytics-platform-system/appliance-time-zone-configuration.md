---
title: "Конфигурация часового пояса устройства (система платформы аналитики)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cea9eeb9-fe05-4e65-b229-539de02ab20a
caps.latest.revision: "18"
ms.openlocfilehash: 0dc20594fa45375fe07b4ec374da9c752d3cc8b0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="appliance-time-zone-configuration"></a>Конфигурация часового пояса устройства
**Часовой пояс** страница позволяет задать часовой пояс для всех узлов на устройстве SQL Server PDW.  
  
## <a name="to-set-the-time-zone"></a>Задайте часовой пояс  
  
1.  Запустите диспетчер конфигурации. Дополнительные сведения см. в разделе [запустить диспетчер конфигурации &#40; Система платформы аналитики &#41; ](launch-the-configuration-manager.md).  
  
2.  Остановка служб устройства с помощью **состояние служб** страницы в Configuration Manager. В разделе [PDW служб состояния &#40; Система платформы аналитики &#41; ](pdw-services-status.md) инструкции.  
  
3.  В левой области Configuration Manager щелкните **часовой пояс**. Выберите нужный часовой пояс из **часовой пояс** раскрывающееся меню. В зависимости от вашего расположения можно также установите флажок рядом с **автоматической настройки часов на летнее время**.  
  
4.  Нажмите кнопку **применить** для сохранения изменений.  
  
5.  Перезапустите службы устройства с помощью **состояние служб** страницы в Configuration Manager. Если планируется также изменить права доступа, это можно сделать перед перезапуском устройства.  
  
![Время устройств DWConfig](./media/appliance-time-zone-configuration/SQL_Server_PDW_DWConfig_ApplTopTime.png "SQL_Server_PDW_DWConfig_ApplTopTime")  
  
## <a name="see-also"></a>См. также:  
[Запустите диспетчер конфигурации &#40; Система платформы аналитики &#41;](launch-the-configuration-manager.md)  
  

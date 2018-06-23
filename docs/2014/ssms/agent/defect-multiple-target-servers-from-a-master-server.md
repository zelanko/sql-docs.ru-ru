---
title: Отключение нескольких целевых серверов от главного | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
- multiple target server defections
ms.assetid: 61a3713b-403a-4806-bfc4-66db72ca1156
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3b43999ba899edd263d7dcacd8ba6150fb299bae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102138"
---
# <a name="defect-multiple-target-servers-from-a-master-server"></a>Defect Multiple Target Servers from a Master Server
  В этом разделе описывается, как исключить несколько целевых серверов из конфигурации администрирования нескольких серверов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Запустите эту процедуру с главного сервера.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-defect-multiple-target-servers-from-a-master-server"></a>Отключение нескольких целевых серверов от главного  
  
1.  В **Обозревателе объектов**разверните главный сервер.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**, укажите пункт **Администрирование нескольких серверов**, а затем выберите пункт **Управление целевыми серверами**.  
  
3.  Щелкните **Отправить инструкции**и в списке **Тип инструкции** выберите **Отключить**.  
  
4.  В пункте **Адресаты**выполните одно из следующих действий:  
  
    -   щелкните **Все целевые серверы** , чтобы отключить от главного сервера все целевые (этот параметр используется в случае, когда нужно полностью удалить установленную текущую конфигурацию администрирования нескольких серверов);  
  
    -   щелкните **Эти целевые серверы**, а затем соответствующий пункт **Выбрать** , чтобы отключить от главного сервера некоторые, но не все целевые серверы.  
  
## <a name="see-also"></a>См. также  
 [Создание многосерверной среды](create-a-multiserver-environment.md)   
 [Автоматизация администрирования в масштабах предприятия](automated-administration-across-an-enterprise.md)   
 [Отключение целевого сервера от главного сервера](defect-a-target-server-from-a-master-server.md)  
  
  
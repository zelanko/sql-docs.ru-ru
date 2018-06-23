---
title: Шаг 5. Тестирование обновленных пакетов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 683e52e5-1c7e-49ab-9ffe-6a450a1c5776
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7db13e319b07a605172746a650c0292dc7f2bfd8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097590"
---
# <a name="step-5-testing-the-updated-packages"></a>Шаг 5. Тестирование обновленных пакетов
  Перед тем как перейти к следующему занятию, в котором вы создадите пакет развертывания, чтобы установить учебные пакеты на целевой компьютер, нужно проверить пакеты. В этой задаче вы выполните пакеты DataTransfer.dtsx и LoadXMLData, которые добавлены в проект учебного развертывания и для которых было выполнено расширение конфигураций.  
  
 По мере выполнения пакетов каждый исполняемый объект становится зеленым. Когда все исполняемые объекты станут зелеными, это будет значить, что пакет выполнен полностью. Просмотреть ход выполнения пакета на вкладке **Выполнение** .  
  
 Если выполнение пакетов завершилось неудачно, нужно исправить их, перед тем как перейти к следующему занятию.  
  
### <a name="to-run-the-datatransfer-package"></a>Выполнение пакета DataTransfer  
  
1.  В обозревателе решений выберите DataTransfer.dtsx.  
  
2.  В меню **Отладка** выберите пункт **Запустить отладку**.  
  
3.  После окончания работы пакета выберите в меню **Отладка** пункт **Остановить отладку**.  
  
### <a name="to-run-the-loadxmldata-package"></a>Выполнение пакета LoadXMLData  
  
1.  В обозревателе решений выберите LoadXMLData.dtsx.  
  
2.  В меню **Отладка** выберите пункт **Запустить отладку**.  
  
3.  После окончания работы пакета выберите в меню **Отладка** пункт **Остановить отладку**.  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Занятие 2. Создание пакета развертывания](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
  
![Значок служб Integration Services (маленький)](media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться установка последних со службами Integration Services** <br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services в MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  
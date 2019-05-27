---
title: Шаг 5. Тестирование обновленных пакетов | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 683e52e5-1c7e-49ab-9ffe-6a450a1c5776
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 40884a52395aee9bb45338f5c56d2709f3d4d956
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65722958"
---
# <a name="lesson-1-5---testing-the-updated-packages"></a>Занятие 1–5. Тестирование обновленных пакетов

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
[Занятие 2. Создание пакета развертывания в службах SSIS](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
  
  
  

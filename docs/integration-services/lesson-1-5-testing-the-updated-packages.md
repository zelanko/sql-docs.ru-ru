---
description: Занятие 1–5. Тестирование обновленных пакетов
title: Шаг 5. Тестирование обновленных пакетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 683e52e5-1c7e-49ab-9ffe-6a450a1c5776
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2a8179b40407e0f2ed012b1b493a5a39434f5cb9
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "88390750"
---
# <a name="lesson-1-5---testing-the-updated-packages"></a>Занятие 1–5. Тестирование обновленных пакетов

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]


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
  
  
  

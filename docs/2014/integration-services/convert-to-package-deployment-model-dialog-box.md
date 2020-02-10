---
title: Диалоговое окно «преобразовать в модель развертывания пакета» | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.bids.converttolegacydeployment.f1
ms.assetid: 9e60a34a-10f7-48d1-966f-b3ff236ab4b7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: dfe1f6e5b752284b6bb0feec96f4f3dfd67cc4f6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66060350"
---
# <a name="convert-to-package-deployment-model-dialog-box"></a>Преобразовать в модель диалоговое окно "пакет развертывания"
  С помощью команды **Преобразовать в модель развертывания пакетов** можно выполнить преобразование пакета в модель развертывания пакетов после проверки проекта и каждого пакета в проекте на совместимость с данной моделью. Если пакет использует специальные функции в модели развертывания проекта, такие как параметры, то пакет невозможно преобразовать.  
  
## <a name="task-list"></a>Список задач  
 Преобразование пакета в модель развертывания пакетов выполняется в два этапа.  
  
1.  При выборе команды **Преобразовать в модель развертывания пакетов** из меню **Проект** выполняется проверка проекта и каждого пакета на совместимость с этой моделью. Результаты отображаются в таблице **Результаты** .  
  
     Если проект или пакеты не прошли проверку на совместимость, щелкните **Ошибка** в столбце **Результат** для получения дополнительных сведений. Нажмите кнопку **Сохранить отчет** для сохранения копии этих сведений в текстовый файл.  
  
2.  Если проект и все пакеты прошли испытание на совместимость, нажмите кнопку **ОК** для преобразования пакета.  
  
> [!NOTE]  
>  Для преобразования проекта в модель развертывания проектов воспользуйтесь **Мастером преобразования проекта служб Integration Services**. Дополнительные сведения см. в статье [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md).  
  
## <a name="see-also"></a>См. также:  
 [Развертывание проектов и пакетов](packages/deploy-integration-services-ssis-projects-and-packages.md)   
 [Развертывание пакетов &#40;&#41;SSIS](packages/legacy-package-deployment-ssis.md)   
 [Мастером преобразования проекта служб Integration Services](../../2014/integration-services/integration-services-project-conversion-wizard.md)  
  
  

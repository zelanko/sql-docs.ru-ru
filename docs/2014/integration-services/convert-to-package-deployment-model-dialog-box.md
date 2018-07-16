---
title: Преобразовать в пакет развертывания модели диалоговое окно | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ssis.bids.converttolegacydeployment.f1
ms.assetid: 9e60a34a-10f7-48d1-966f-b3ff236ab4b7
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1cb982b23645821f6c24c51b4ce4402336c08ea5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233866"
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
  
## <a name="see-also"></a>См. также  
 [Развертывание проектов и пакетов](packages/deploy-integration-services-ssis-projects-and-packages.md)   
 [Развертывания пакета &#40;служб SSIS&#41;](packages/legacy-package-deployment-ssis.md)   
 [Мастер преобразования проекта служб Integration Services](../../2014/integration-services/integration-services-project-conversion-wizard.md)  
  
  

---
title: Преобразовать в пакет развертывания модели диалоговое | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.bids.converttolegacydeployment.f1
ms.assetid: 9e60a34a-10f7-48d1-966f-b3ff236ab4b7
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 69d64b35f39c86b9070df9c9fcfacfcf9a7d68f8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102247"
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
 [Пакет развертывания &#40;служб SSIS&#41;](packages/legacy-package-deployment-ssis.md)   
 [Мастер преобразования проекта служб Integration Services](../../2014/integration-services/integration-services-project-conversion-wizard.md)  
  
  
---
title: Отладка кода модуля обработки данных | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- debugging data processing extensions [Reporting Services]
- troubleshooting [Reporting Services], data processing extensions
- data processing extensions [Reporting Services], debugging
ms.assetid: e963e205-9ae0-446d-97df-028a1d2727d9
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2ea04867f59393a4494ea6f2d179d1ffa8b80e9c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47743732"
---
# <a name="debugging-data-processing-extension-code"></a>Отладка кода модуля обработки данных
  Платформа [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] предоставляет несколько средств отладки, которые помогают анализировать код в модуле обработки данных и искать в нем ошибки. Какое средство будет наилучшим, зависит от того, что нужно выполнить. В этом примере используется [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].  
  
#### <a name="to-debug-your-data-processing-extension-code"></a>Отладка кода модуля обработки данных  
  
1.  Запустите среду [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] и откройте проект модуля обработки данных.  
  
2.  Постройте проект и разверните в конструкторе отчетов сборку модуля обработки данных и сопроводительный PDB-файл. Дополнительные сведения о развертывании см. в статье [Практическое руководство. Развертывание модуля обработки данных в конструкторе отчетов](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-report-designer.md).  
  
3.  Откройте новый проект отчета в среде [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], оставив код модуля обработки данных открытым в отдельном окне среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
4.  Перейдите к окну среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], содержащему проект модуля обработки данных, и установите в коде несколько точек останова.  
  
5.  Пока окно с проектом модуля обработки данных остается активным, в меню **Отладка** выберите команду **Присоединить к процессу**.  
  
     Откроется диалоговое окно **Присоединение к процессу**.  
  
6.  Выберите из списка процессов devenv.exe, который соответствует проекту отчета, и нажмите кнопку **Присоединить**.  
  
7.  Определите источник данных отчета на вкладке **Данные отчета** в проекте отчета. Чтобы выполнить запрос к пользовательскому источнику данных, скорее всего, будет использоваться обычный конструктор запросов. Будет запущен отладчик и начнется выполнение кода с учетом заданных точек останова.  
  
8.  Перемещайтесь по шагам кода с помощью клавиши F11. Дополнительные сведения об использовании среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] для отладки см. в документации по среде [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Развертывание модуля обработки данных](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

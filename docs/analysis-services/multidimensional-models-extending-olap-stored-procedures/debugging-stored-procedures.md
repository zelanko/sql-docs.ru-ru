---
title: "Отладка хранимых процедур | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- debugging stored procedures [Analysis Services]
- stored procedures [Analysis Services], debugging
ms.assetid: 34f51b85-02b3-40dd-bf93-375a9e522385
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7b605ee9a2af577048c03d406ff628b1d279a68e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="debugging-stored-procedures"></a>Отладка хранимых процедур
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] хранимые процедуры, фактически библиотеки CLR или COM (обычно DLL), написанные на C# (или любом другом языке CLR или COM). Таким образом, отладка хранимой процедуры практически аналогична отладке любого другого приложения в среде отладки Visual Studio. Отладка хранимых процедур в среде разработки Visual Studio производится с использованием интегрированных функций отладки. Они позволяют осуществлять остановку процедуры в определенных местах, контролировать значения в памяти и регистрах, изменять переменные, следить за трафиком сообщений и подробно анализировать работу кода.  
  
### <a name="to-debug-a-stored-procedure"></a>Отладка хранимой процедуры  
  
1.  Откройте проект, используемый для создания библиотеки DLL, в среде Visual Studio.  
  
2.  Создайте точки прерывания в методе или функции, соответствующей процедуре, которую необходимо отладить.  
  
3.  Используйте среду Visual Studio для создания отладочной сборки библиотеки DLL хранимой процедуры.  
  
4.  Разверните эту библиотеку DLL на сервере. Дополнительные сведения о развертывании библиотеки DLL на сервере см. в разделе [Создание хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/creating-stored-procedures.md).  
  
5.  Необходимо приложение, вызывающее хранимую процедуру, подлежащую тестированию. При его отсутствии можно использовать редактор запросов многомерных выражений в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для создания запроса многомерных выражений, вызывающего хранимую процедуру, которую необходимо протестировать.  
  
6.  В среде Visual Studio подключитесь к процессу служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (Msmdsrv.exe).  
  
    1.  Из **отладки** меню, выберите **toProcess соединение**.  
  
    2.  В **toProcess соединение** выберите **Показать процессы всех пользователей**.  
  
    3.  В **доступные процессы** в списке **процесс** столбец, нажмите кнопку **Msmdsrv.exe**. Если на сервере несколько экземпляров служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], то определить необходимый процесс можно по идентификатору экземпляра.  
  
    4.  В **присоединить** текстовое поле, убедитесь, что выбран правильный тип программы. DLL-Библиотеки CLR нажмите **выберите**, нажмите кнопку **отладить код следующих типов**, нажмите кнопку **управляемое**, нажмите кнопку **ОК**. DLL-Библиотеки COM нажмите **выберите**, нажмите кнопку **отладить код следующих типов**, нажмите кнопку **собственного**, нажмите кнопку **ОК**.  
  
    5.  Нажмите кнопку **присоединения**.  
  
7.  В службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] запустите программу или скрипт многомерных выражений, вызывающий хранимую процедуру. Отладчик останавливается, когда достигает строку, содержащую точку прерывания. Можно оценить переменные в окне наблюдения, просмотреть локальные значения и проверить шаги кода.  
  
 При возникновении проблем с отладкой библиотеки убедитесь, что соответствующий файл базы данных программ (PDB-файл) скопирован в место развертывания на сервере. Если этот файл не был скопирован во время регистрации или развертывания, то его необходимо скопировать вручную в то же место, где находится библиотека DLL. Для собственного кода (COM DLL) PDB-файл находится в подкаталоге \debug. Для управляемого (CLR DLL) — он находится в подкаталоге \WINDEBUG.  
  
## <a name="see-also"></a>См. также:  
 [Управление сборками многомерной модели](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Определение хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  

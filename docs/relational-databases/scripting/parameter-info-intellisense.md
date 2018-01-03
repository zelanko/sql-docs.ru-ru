---
title: "Сведения о параметре (IntelliSense) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Parameter Info option [IntelliSense]
- stored function parameter completion [Intellisense]
- language references [SQL Server]
- IntelliSense [SQL Server], Parameter Info option
ms.assetid: 56c2aac9-c65c-4679-b62c-d9f689876dde
caps.latest.revision: "33"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9fea9f7c736c3585403b17999673eef41420c3a7
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="parameter-info-intellisense"></a>Сведения о параметре (технология IntelliSense)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Параметр **Сведения о параметре** технологии [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense позволяет открыть список параметров, содержащий сведения о количестве, именах и типах параметров функции или хранимой процедуры. При вводе функции или системной хранимой процедуры следующий обязательный параметр отображается полужирным шрифтом.  
  
 Список параметров отображается также и для вложенных функций. Если функция вводится в качестве параметра другой функции, в списке параметров перечисляются параметры для этой вложенной функции. Затем, когда список параметров вложенной функции заполнен, в списке продолжается отображение параметров внешней функции.  
  
#### <a name="to-view-parameter-info-for-functions-or-stored-procedures"></a>Просмотр сведений о параметрах для функций или хранимых процедур  
  
1.  После имени функции введите открывающую скобку, как это обычно делается для открытия списка параметров. Набрав имя хранимой процедуры, введите пробел, как это обычно делается для получения данных о параметрах процедур.  
  
     Технология IntelliSense отобразит полное объявление функции либо параметры хранимой процедуры во всплывающем окне сразу после позиции ввода. Первый параметр в списке будет выделен полужирным шрифтом.  
  
2.  По мере набора параметров выделение будет смещаться к следующему параметру, который необходимо ввести.  
  
3.  Нажав клавишу ESC, в любой момент можно закрыть список, в противном случае набор будет продолжен до заполнения функции.  
  
     Для функции ввод закрывающей скобки закроет список параметров.  
  
#### <a name="to-manually-start-parameter-info"></a>Открытие списка «Сведения о параметре» вручную  
  
1.  В меню **Правка** выберите пункт **IntelliSense** , а затем пункт **Сведения о параметре**.  
  
2.  Нажмите сочетание клавиш CTRL + SHIFT + ПРОБЕЛ.  
  
 Дополнительные сведения см. в статье [Настройка IntelliSense (среда SQL Server Management Studio)](../../relational-databases/scripting/configure-intellisense-sql-server-management-studio.md).  
  
> [!NOTE]  
>  Параметр **Сведения о параметре** доступен только для редактора запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и редактора XML-запросов.  
  
  

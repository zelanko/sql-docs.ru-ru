---
title: Отмена запрета предупреждений для пользовательских отчетов | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d303321941668d5115c3796022f70195b4a0d066
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194858"
---
# <a name="unsuppress-run-custom-report-warnings"></a>Отмена подавления предупреждений для пользовательских отчетов
  Для пользовательских отчетов предусмотрено два типа предупреждающих диалоговых окон. В этом разделе описано, как отменить подавление отображения этих полей в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 По умолчанию перед запуском пользовательского отчета отображается диалоговое окно **Запустить пользовательский отчет** . Если установить флажок **Больше не показывать это предупреждение** , то это диалоговое окно больше отображаться не будет. Также по умолчанию диалоговое окно **Запустить пользовательский отчет** отображается, если после открытия одного пользовательского отчета нажать ссылку для открытия другого отчета. В этом диалоговом окне отображается полный путь к файлу пользовательского детализированного отчета. Если установить флажок **Больше не показывать это предупреждение** , то это диалоговое окно больше отображаться не будет.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a>Отмена подавления основного диалогового окна предупреждения для пользовательских отчетов  
  
1.  Подключиться к \< *сервера*>\\<*общего ресурса*>|\<*диска*> \ Documents and Settings\\< UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml.  
  
2.  Щелкните правой кнопкой мыши `reports.xml`, а затем нажмите кнопку **изменить**.  
  
3.  Изменение**\<SuppressWarning > значение true,\</suppresswarning > для \<SuppressWarning > false\</suppresswarning >**.  
  
4.  Перезапустите [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a>Отмена подавления диалогового окна предупреждений для детализированных пользовательских отчетов  
  
1.  Подключиться к \< *сервера*>\\<*общего ресурса*>|\<*диска*> \ Documents and Settings\\< UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml.  
  
2.  Щелкните правой кнопкой мыши `reports.xml`и нажмите кнопку **изменить**.  
  
3.  Изменение  **\<SuppressDrillthroughWarning > значение true,\</SuppressDrillthroughWarning > для \<SuppressDrillthroughWarning > false\</SuppressDrillthroughWarning >**.  
  
4.  Перезапустите [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Пользовательские отчеты в среде Management Studio](custom-reports-in-management-studio.md)   
 [Добавление пользовательского отчета в среде Management Studio](add-a-custom-report-to-management-studio.md)   
 [Использование пользовательских отчетов для свойств узлов обозревателя объектов](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
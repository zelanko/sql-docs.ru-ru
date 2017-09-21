---
title: "Использование связей значений в составном домене | Microsoft Docs"
ms.custom: 
ms.date: 11/22/2011
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dqs.dm.cdvaluerelations.f1
ms.assetid: 5ee468f0-8538-4620-90e8-63f466c9000e
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c42159a2477e4eeba0afbaa536427cace2a5aafc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="use-value-relations-in-a-composite-domain"></a>Использование связей значений в составном домене
  В этом разделе описываются способы просмотра сочетаний значений, обнаруженных для составного домена в процессе обнаружения знаний в службах [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Эта страница показывает количество повторений сочетаний значений. Управление значениями не поддерживается для составных доменов, поэтому операции с этими значениями выполнить не удастся.  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
 Чтобы просмотреть связи значений, необходимо создать и открыть составной домен.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Для просмотра связей значений в составном домене необходимо иметь роль dqs_kb_editor или dqs_administrator в базе данных DQS_MAIN.  
  
##  <a name="Use"></a> Просмотр связей значений  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Запуск клиентского приложения Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На главном экране клиента [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] откройте или создайте базу знаний. Выберите операцию **Управление доменами** , а затем нажмите кнопку **Открыть** или **Создать**. Дополнительные сведения см. в разделе [Create a Knowledge Base](../data-quality-services/create-a-knowledge-base.md) или [Open a Knowledge Base](../data-quality-services/open-a-knowledge-base.md).  
  
3.  Из **Списка доменов** на странице **Управление доменами** выберите составной домен, для которого надо создать доменное правило, или просто создайте новый составной домен. Если нужно создать новый домен, см. раздел [Create a Composite Domain](../data-quality-services/create-a-composite-domain.md).  
  
4.  Перейдите на вкладку **Связи значений** .  
  
5.  Просмотрите частоту повторения каждого сочетания значений.  
  
    > [!NOTE]  
    >  В таблице **Значение** показаны все сочетания значений, существующие в составном домене. Каждое значение отображается в отдельном домене, к которому оно относится. По умолчанию связи значений в таблице сортируются по частоте, но вы можете щелкнуть другой столбец, чтобы сортировать по этому столбцу. Отображаются только значения с частотой, большей или равной 20.  
  
6.  Изменить какие-либо значения в этой таблице нельзя. Если вы выполнили другие операции, нажмите кнопку **Готово** для завершения действия по управлению доменами. В противном случае нажмите кнопку **Отмена**.  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После просмотра связей значений  
 После просмотра связей значений в домене можно выполнить другие задачи по управлению доменами, произвести обнаружение знаний для добавления набора знаний в домен или добавить в домен политику сопоставления. Дополнительные сведения см. в разделах [Обнаружение набора знаний](../data-quality-services/perform-knowledge-discovery.md), [Управление доменом](../data-quality-services/managing-a-domain.md) и [Создание политики сопоставления](../data-quality-services/create-a-matching-policy.md).  
  
  

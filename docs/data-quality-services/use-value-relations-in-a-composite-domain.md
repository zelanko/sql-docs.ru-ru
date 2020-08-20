---
description: Использование связей значений в составном домене
title: Использование связей значений в составном домене
ms.date: 11/22/2011
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.dm.cdvaluerelations.f1
ms.assetid: 5ee468f0-8538-4620-90e8-63f466c9000e
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 67d6d4743fc373afd0ac008a72c7d97751b8ac29
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466602"
---
# <a name="use-value-relations-in-a-composite-domain"></a>Использование связей значений в составном домене

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sqlserver.md)]

  В этом разделе описываются способы просмотра сочетаний значений, обнаруженных для составного домена в процессе обнаружения знаний в службах [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Эта страница показывает количество повторений сочетаний значений. Управление значениями не поддерживается для составных доменов, поэтому операции с этими значениями выполнить не удастся.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
 Чтобы просмотреть связи значений, необходимо создать и открыть составной домен.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для просмотра связей значений в составном домене необходимо иметь роль dqs_kb_editor или dqs_administrator в базе данных DQS_MAIN.  
  
##  <a name="view-value-relations"></a><a name="Use"></a> Просмотр связей значений  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Запустите приложение Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На главном экране клиента [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] откройте или создайте базу знаний. Выберите операцию **Управление доменами** , а затем нажмите кнопку **Открыть** или **Создать**. Дополнительные сведения см. в разделе [Создание базы знаний](../data-quality-services/create-a-knowledge-base.md) или [Открытие базы знаний](../data-quality-services/open-a-knowledge-base.md).  
  
3.  Из **Списка доменов** на странице **Управление доменами** выберите составной домен, для которого надо создать доменное правило, или просто создайте новый составной домен. Если нужно создать новый домен, см. раздел [Create a Composite Domain](../data-quality-services/create-a-composite-domain.md).  
  
4.  Перейдите на вкладку **Связи значений** .  
  
5.  Просмотрите частоту повторения каждого сочетания значений.  
  
    > [!NOTE]  
    >  В таблице **Значение** показаны все сочетания значений, существующие в составном домене. Каждое значение отображается в отдельном домене, к которому оно относится. По умолчанию связи значений в таблице сортируются по частоте, но вы можете щелкнуть другой столбец, чтобы сортировать по этому столбцу. Отображаются только значения с частотой, большей или равной 20.  
  
6.  Изменить какие-либо значения в этой таблице нельзя. Если вы выполнили другие операции, нажмите кнопку **Готово** для завершения действия по управлению доменами. В противном случае нажмите кнопку **Отмена**.  
  
##  <a name="follow-up-after-viewing-value-relations"></a><a name="FollowUp"></a> Дальнейшие действия. После просмотра связей значений  
 После просмотра связей значений в домене можно выполнить другие задачи по управлению доменами, произвести обнаружение знаний для добавления набора знаний в домен или добавить в домен политику сопоставления. Дополнительные сведения см. в разделах [Обнаружение набора знаний](../data-quality-services/perform-knowledge-discovery.md), [Управление доменом](../data-quality-services/managing-a-domain.md) и [Создание политики сопоставления](../data-quality-services/create-a-matching-policy.md).  
  
  

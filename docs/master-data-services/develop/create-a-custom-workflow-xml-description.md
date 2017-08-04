---
title: "Описание XML настраиваемого рабочего процесса (Master Data Services) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: e267e5f4-38bb-466d-82e8-871eabeec07e
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ca6f208bab4ed0b7932d3bd5f7e9a911b8b2c8af
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-custom-workflow---xml-description"></a>Создание настраиваемого рабочего процесса - XML-описание
  В веб-службе [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] метод <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> вызывается службой SQL Server MDS Workflow Integration Service при запуске рабочего процесса. Этот метод получает метаданные и данные об элементе, вызвавшем срабатывание бизнес-правила рабочего процесса, в виде блока XML-данных. Примеры кода, который реализует обработчик рабочего процесса см. в разделе [пользовательского рабочего процесса примера &#40; Службы Master Data Services &#41; ](../../master-data-services/develop/create-a-custom-workflow-example.md).  
  
 В следующем примере показано, как могут выглядеть XML-данные, которые отправляются обработчику рабочего процесса.  
  
```scr  
<ExternalAction>  
  <Type>TEST</Type>  
  <SendData>1</SendData>  
  <Server_URL>This is my test!</Server_URL>  
  <Action_ID>Test Workflow</Action_ID>  
  <Model_ID>5</Model_ID>  
  <Model_Name>Customer</Model_Name>  
  <Entity_ID>34</Entity_ID>  
  <Entity_Name>Customer</Entity_Name>  
  <Version_ID>8</Version_ID>  
  <MemberType_ID>1</MemberType_ID>  
  <Member_ID>12</Member_ID>  
  <MemberData>  
    <ID>12</ID>  
    <Version_ID>8</Version_ID>  
    <ValidationStatus_ID>3</ValidationStatus_ID>  
    <ChangeTrackingMask>0</ChangeTrackingMask>  
    <EnterDTM>2011-02-25T20:16:36.650</EnterDTM>  
    <EnterUserID>2</EnterUserID>  
    <EnterUserName>MyUserName</EnterUserName>  
    <EnterUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</EnterUserMuid>  
    <EnterVersionId>8</EnterVersionId>  
    <EnterVersionName>VERSION_1</EnterVersionName>  
    <EnterVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</EnterVersionMuid>  
    <LastChgDTM>2011-02-25T20:16:36.650</LastChgDTM>  
    <LastChgUserID>2</LastChgUserID>  
    <LastChgUserName>MyUserName</LastChgUserName>  
    <LastChgUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</LastChgUserMuid>  
    <LastChgVersionId>8</LastChgVersionId>  
    <LastChgVersionName>VERSION_1</LastChgVersionName>  
    <LastChgVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</LastChgVersionMuid>  
    <Name>Test Customer</Name>  
    <Code>TC</Code>  
  </MemberData>  
</ExternalAction>  
```  
  
 В следующей таблице описаны некоторые теги, которые содержатся в этих XML-данных.  
  
|Тег|Description|  
|---------|-----------------|  
|\<Тип >|Текст, введенный в **тип рабочего процесса** текстовое поле в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] для идентификации какие пользовательского рабочего процесса сборки для загрузки.|  
|\<SendData >|Значение типа Boolean, контролируются **включать данные элемента в сообщении** флажок в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]. Значение 1 означает, что \<MemberData > раздел отправки; в противном случае \<MemberData > не отправляется раздел.|  
|< Server_URL >|Текст, введенный в **рабочего процесса сайта** текстовое поле в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].|  
|< Action_ID >|Текст, введенный в **имя рабочего процесса** текстовое поле в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].|  
|\<MemberData >|Содержит данные элемента, вызвавшего срабатывание действия рабочего процесса. Это включается только в том случае, если значение \<SendData > равно 1.|  
|\<Введите*xxx*>|Этот набор тегов содержит метаданные о создании элемента, например дату создания и автора.|  
|\<LastChg*xxx*>|Этот набор тегов содержит метаданные о последнем изменении, внесенном в элемент, например дату внесения изменения и автора.|  
|\<Имя >|Первый атрибут элемента, который был изменен. Этот пример элемента содержит только атрибуты Name и Code.|  
|\<Код >|Следующий атрибут элемента, который был изменен. Если бы этот пример элемента содержал больше атрибутов, то они следовали бы за первым.|  
  
## <a name="see-also"></a>См. также:  
 [Создать пользовательский рабочий процесс &#40; Службы Master Data Services &#41;](../../master-data-services/develop/create-a-custom-workflow-master-data-services.md)   
 [Пример настраиваемого рабочего процесса &#40; Службы Master Data Services &#41;](../../master-data-services/develop/create-a-custom-workflow-example.md)  
  
  

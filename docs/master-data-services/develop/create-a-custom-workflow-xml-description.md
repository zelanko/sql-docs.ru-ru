---
title: Описание XML настраиваемого рабочего процесса
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: reference
ms.assetid: e267e5f4-38bb-466d-82e8-871eabeec07e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f7c49f9b2831942552844e6bb479d139988d84c7
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897419"
---
# <a name="create-a-custom-workflow---xml-description"></a>Создание настраиваемого рабочего процесса — описание XML

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] метод [Microsoft. MasterDataServices. Воркфловтипикстендер. Иворкфловтипикстендер. стартворкфлов *](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) вызывается службой интеграции рабочего процесса MDS SQL Server при запуске рабочего процесса. Этот метод получает метаданные и данные об элементе, вызвавшем срабатывание бизнес-правила рабочего процесса, в виде блока XML-данных. Пример кода, который реализует обработчик рабочего процесса, см. в разделе [Пример пользовательского рабочего процесса (службы Master Data Services)](../../master-data-services/develop/create-a-custom-workflow-example.md).  
  
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
  
|Тег|Описание|  
|---------|-----------------|  
|\<Type>|Текст, введенный в поле **Тип рабочего процесса** в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], указывает пользовательскую сборку рабочего процесса, которая будет загружаться.|  
|\<SendData>|Логическое значение, которое в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] управляется флажком **Включить в сообщение данные элементов**. Значение 1 означает, что \<MemberData> раздел отправляется; в противном случае \<MemberData> раздел не отправляется.|  
|<Server_URL>|Текст, введенный в поле **Сайт рабочего процесса** в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].|  
|<Action_ID>|Текст, введенный в поле **Имя рабочего процесса** в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].|  
|\<MemberData>|Содержит данные элемента, вызвавшего срабатывание действия рабочего процесса. Он включается, только если значение \<SendData> равно 1.|  
|\<Enter*xxx*>|Этот набор тегов содержит метаданные о создании элемента, например дату создания и автора.|  
|\<LastChg*xxx*>|Этот набор тегов содержит метаданные о последнем изменении, внесенном в элемент, например дату внесения изменения и автора.|  
|\<Name>|Первый атрибут элемента, который был изменен. Этот пример элемента содержит только атрибуты Name и Code.|  
|\<Code>|Следующий атрибут элемента, который был изменен. Если бы этот пример элемента содержал больше атрибутов, то они следовали бы за первым.|  
  
## <a name="see-also"></a>См. также  
 [Создание настраиваемого &#40;рабочего процесса Master Data Services&#41;](../../master-data-services/develop/create-a-custom-workflow-master-data-services.md)   
 [Пример настраиваемого рабочего процесса (службы Master Data Services)](../../master-data-services/develop/create-a-custom-workflow-example.md)  
  
  

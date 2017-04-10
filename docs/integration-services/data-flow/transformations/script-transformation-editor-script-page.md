---
title: "Редактор преобразования &#171;Скрипт&#187; (страница &#171;Скрипт&#187;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.scriptcomponent.script.f1"
helpviewer_keywords: 
  - "редактор преобразования «Скрипт»"
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# Редактор преобразования &#171;Скрипт&#187; (страница &#171;Скрипт&#187;)
  Используйте вкладку **Скрипт** в диалоговом окне **Редактор преобразования «Скрипт»** для указания скрипта и связанных с ним свойств.  
  
 Дополнительные сведения о компоненте скрипта см. в разделах [Script Component](../../../integration-services/data-flow/transformations/script-component.md) и [Configuring the Script Component in the Script Component Editor](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md). Дополнительные сведения о программировании компонента скрипта см. в разделе [Extending the Data Flow with the Script Component](../../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
## Параметры  
 **Свойства**  
 Просмотрите и измените свойства преобразования «Скрипт». Многие отображаемые параметры доступны только для чтения. Следующие свойства могут быть изменены.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Description**|Опишите преобразование «Скрипт», его назначение.|  
|**LocaleID**|Укажите локаль, предоставляющую сведения о регионе, используемые для сортировки и преобразования даты и времени.|  
|**Название**|Введите описательное имя компонента.|  
|**ValidateExternalMetadata**|Укажите, будет ли преобразование «Скрипт» во время разработки проверять метаданные столбца относительно источников внешних данных. Значение **false** откладывает проверку до времени выполнения.|  
|**ReadOnlyVariables**|Введите через запятую список переменных, доступ к которым в ходе преобразования «Скрипт» возможен только для чтения.<br /><br /> Примечание. В именах переменных учитывается регистр.|  
|**ReadWriteVariables**|Введите через запятую список переменных, доступ к которым в ходе преобразования «Скрипт» возможен как для чтения, так и для записи.<br /><br /> Примечание. В именах переменных учитывается регистр.|  
|**ScriptLanguage**|Язык скрипта, используемый компонентом скрипта.<br /><br /> Чтобы установить значение по умолчанию языка скрипта для компонентов скрипта и задач «Скрипт», воспользуйтесь параметром **Язык скрипта** страницы **Общие** диалогового окна **Параметры** .|  
|**UserComponentTypeName**|Определяет класс <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> и сборку **Microsoft.SqlServer.TxScript**, поддерживающие инфраструктуру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
 **Изменение скрипта**  
 Чтобы создать или изменить скрипт, воспользуйтесь набором средств [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] для работы с приложениями.  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Выбор типа компонента скрипта](../../../integration-services/data-flow/transformations/select-script-component-type.md)   
 [Редактор преобразования "Скрипт" (страница "Входные столбцы")](../../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md)   
 [Редактор преобразования "Скрипт" (страница "Входы и выходы")](../../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md)   
 [Редактор преобразования "Скрипт" (страница "Диспетчеры соединений")](../../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md)   
 [Дополнительные примеры компонента скрипта](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
---
title: Редактор преобразования скриптов (страница «скрипт») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.script.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 102988ac347543a4d2e2110d4c8511c398be9348
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48060684"
---
# <a name="script-transformation-editor-script-page"></a>Редактор преобразования «Скрипт» (страница «Скрипт»)
  Используйте вкладку **Скрипт** в диалоговом окне **Редактор преобразования «Скрипт»** для указания скрипта и связанных с ним свойств.  
  
 Дополнительные сведения о компоненте скрипта см. в разделе [компонента скрипта](data-flow/transformations/script-component.md) и [Настройка компонента скрипта в редакторе компонента скрипта](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md). Дополнительные сведения о программировании компонента скрипта, см. в разделе [расширение потока данных в компоненте скрипта](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
## <a name="options"></a>Параметры  
 **Свойства**  
 Просмотрите и измените свойства преобразования «Скрипт». Многие отображаемые параметры доступны только для чтения. Следующие свойства могут быть изменены.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Описание**|Опишите преобразование «Скрипт», его назначение.|  
|**LocaleID**|Укажите локаль, предоставляющую сведения о регионе, используемые для сортировки и преобразования даты и времени.|  
|**Название**|Введите описательное имя компонента.|  
|**ValidateExternalMetadata**|Укажите, будет ли преобразование «Скрипт» во время разработки проверять метаданные столбца относительно источников внешних данных. Значение `false` откладывает проверку до времени выполнения.|  
|**ReadOnlyVariables**|Введите через запятую список переменных, доступ к которым в ходе преобразования «Скрипт» возможен только для чтения.<br /><br /> Примечание. В именах переменных учитывается регистр.|  
|**ReadWriteVariables**|Введите через запятую список переменных, доступ к которым в ходе преобразования «Скрипт» возможен как для чтения, так и для записи.<br /><br /> Примечание. В именах переменных учитывается регистр.|  
|**ScriptLanguage**|Язык скрипта, используемый компонентом скрипта.<br /><br /> Чтобы установить значение по умолчанию языка скрипта для компонентов скрипта и задач «Скрипт», воспользуйтесь параметром **Язык скрипта** страницы **Общие** диалогового окна **Параметры** . Дополнительные сведения см. в разделе [General Page](general-page-of-integration-services-designers-options.md).|  
|**UserComponentTypeName**|Определяет класс <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> и сборку `Microsoft.SqlServer.TxScript`, поддерживающую инфраструктуру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|  
  
 **Изменение скрипта**  
 Чтобы создать или изменить скрипт, воспользуйтесь набором средств [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для работы с приложениями.  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Выбор типа компонента скрипта](../../2014/integration-services/select-script-component-type.md)   
 [Редактор преобразования "скрипт" &#40;ввода страница "столбцы"&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md)   
 [Редактор преобразования "скрипт" &#40;входных и выходных данных страницы&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md)   
 [Редактор преобразования "скрипт" &#40;страница «Диспетчеры соединений»&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md)   
 [Дополнительные примеры компонента скрипта](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  

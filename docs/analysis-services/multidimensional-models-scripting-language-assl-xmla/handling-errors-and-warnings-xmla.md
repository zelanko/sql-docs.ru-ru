---
title: "Обработка ошибок и предупреждений (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- errors [XML for Analysis]
- inline errors [XMLA]
- SOAP faults [XML for Analysis]
- XML for Analysis, errors
- faults [XML for Analysis]
- messages [XML for Analysis]
- XMLA, errors
- warnings [XML for Analysis]
- inline warnings [XMLA]
ms.assetid: ab895282-098d-468e-9460-032598961f45
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e5aa002079080e8c4e3fc4816539fda866e8293b
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="handling-errors-and-warnings-xmla"></a>Обработка ошибок и предупреждений (XMLA)
  Обработка ошибок является обязательным, если XML для аналитики (XMLA) [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) или [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) вызов метода не выполняется, успешно выполняется, но приводит к возникновению ошибки или предупреждения, или выполняется успешно, но возвращает результаты которые содержат ошибки.  
  
|Ошибка|Отчет|  
|-----------|---------------|  
|Вызов метода XMLA не запускается|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Возвращает сообщения об ошибке SOAP, которая содержит сведения о сбое.<br /><br /> Дополнительные сведения см. в разделе разделе [обработка сбоев SOAP](#handling_soap_faults).|  
|Ошибки или предупреждения при успешном вызове метода|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] включает в себя [ошибка](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) или [предупреждение](../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md) элемент для каждой ошибки или предупреждения, соответственно, в [сообщений](../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md) свойство [корневой](../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) элемент содержащий результаты вызова метода.<br /><br /> Дополнительные сведения см. в разделе разделе [обработка ошибок и предупреждений](#handling_errors_and_warnings).|  
|Ошибки в результате при успешном вызове метода|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] включает встроенный **ошибка** или **предупреждение** элемента для ошибки или предупреждения соответственно в предназначенный [ячейки](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) или [строки](../../analysis-services/xmla/xml-elements-properties/row-element-xmla.md) элемент результаты вызова метода.<br /><br /> Дополнительные сведения см. в разделе разделе [обработка встроенных ошибок и предупреждений](#handling_inline_errors_and_warnings).|  
  
##  <a name="handling_soap_faults"></a> Обработка сбоев SOAP  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Возвращает ошибку SOAP, при возникновении следующих ситуаций:  
  
-   Сообщение SOAP, содержащее метод XMLA, имеет неправильный формат, или экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не может провести проверку его правильности.  
  
-   Произошла ошибка связи или другая ошибка, касающаяся сообщения SOAP, содержащего метод XMLA.  
  
-   Метод XMLA не запустился в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Коды сбоев SOAP для XMLA начинаются с «XMLForAnalysis», далее следуют точка и шестнадцатеричный код результата HRESULT. Например, код ошибки `0x80000005` форматируется как `XMLForAnalysis.0x80000005`. Дополнительные сведения о формате сбоев SOAP см. в разделе «Soap Fault» (Сбои Soap) документа «W3C Simple Object Access Protocol (SOAP) 1.1».  
  
### <a name="fault-code-information"></a>Сведения о кодах ошибок  
 В следующей таблице приведены сведения о кодах ошибок XMLA, которые содержатся в разделе подробностей ответа SOAP. Столбцы являются атрибутами ошибки в разделе подробностей сбоя SOAP.  
  
|Имя столбца|Тип|Описание|Значение NULL разрешено<sup>1</sup>|  
|-----------------|----------|-----------------|------------------------------|  
|**ErrorCode**|**UnsignedInt**|Код возврата, указывающий успешное или неудачное выполнение метода. Шестнадцатеричное значение необходимо преобразовать в **UnsignedInt** значение.|нет|  
|**WarningCode**|**UnsignedInt**|Код возврата, указывающий состояние предупреждения. Шестнадцатеричное значение необходимо преобразовать в **UnsignedInt** значение.|Да|  
|**Description**|**String**|Текст ошибки или предупреждения и описание, возвращаемые компонентом, сформировавшим ошибку.|Да|  
|**Source**|**String**|Имя компонента, сформировавшего ошибку или предупреждение.|Да|  
|**HelpFile**|**String**|Путь или URL-адрес к файлу или разделу справки, в котором описывается ошибка или предупреждение.|Да|  
  
 <sup>1</sup> указывает ли данные является обязательным и должен быть возвращен, или ли данных является необязательным и допустима пустая строка, если столбец не применяется.  
  
 Далее приведен пример сбоя SOAP, произошедшего при неудачном завершении вызова метода:  
  
```  
<?xml version="1.0"?>  
   <SOAP-ENV:Envelope  
   xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
   SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
      <SOAP-ENV:Fault>  
         <faultcode>XMLAnalysisError.0x80000005</faultcode>  
         <faultstring>The XML for Analysis provider encountered an error.</faultstring>  
         <faultactor>XML for Analysis Provider</faultactor>  
         <detail>  
<Error  
ErrorCode="2147483653"  
Description="An unexpected error has occurred."  
Source="XML for Analysis Provider"  
HelpFile="" />  
         </detail>  
      </SOAP-ENV:Fault>  
</SOAP-ENV:Envelope>  
```  
  
##  <a name="handling_errors_and_warnings"></a> Обработка ошибок и предупреждений  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Возвращает **сообщений** свойство в **корневой** элемент для команды в случае возникновения следующих ситуаций после запуска этой команды:  
  
-   Сам метод выполнен успешно, но ошибка возникла в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] после успешного вызова метода.  
  
-   Экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращает предупреждение при успешном выполнении команды.  
  
 **Сообщений** свойству предшествует все остальные свойства, содержащиеся в **корневой** элемент и может содержать один или несколько **сообщение** элементов. В свою очередь, каждый **сообщение** может содержать один элемент **ошибка** или **предупреждение** элемент, описывающий ошибки или предупреждения, соответственно, которая произошла для Указанная команда.  
  
 Дополнительные сведения об ошибках и предупреждениях, содержащихся в **сообщений** свойство, в разделе [Messages, элемент &#40; XML для Аналитики &#41; ](../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md).  
  
### <a name="handling-errors-during-serialization"></a>Обработка ошибок во время сериализации  
 Если ошибка возникает после [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляр уже начал сериализацию выходных данных успешно выполненной команды, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращает [исключение](../../analysis-services/xmla/xml-elements-properties/exception-element-xmla.md) элемент в другом пространстве точке ошибки. Затем экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] закрывает все открытые элементы с тем, чтобы XML-документ, отправляемый клиенту, был допустимым. Экземпляр возвращает также **сообщений** элемента, содержащего описание ошибки.  
  
##  <a name="handling_inline_errors_and_warnings"></a> Обработка встроенных ошибок и предупреждений  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Возвращает встроенную **ошибка** или **предупреждение** для команды, если сам метод XMLA выполнен, но произошла ошибка, характерная для элемента данных в результатах, возвращаемых методом на [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляр после успешного вызова метода XMLA.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставляет встроенные **ошибка** и **предупреждение** элементы в случае возникновения проблем, характерных для ячейки или других данных, содержащихся в **корневой** элемента с помощью [ MDDataSet](../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) происходят тип данных, таких как ошибка безопасности или ошибка форматирования для ячейки. В этих случаях [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращает **ошибка** или **предупреждение** элемент в **ячейки** или **строки** элемент, который содержит ошибку или предупреждения, соответственно.  
  
 В следующем примере показан результирующий набор, который содержит ошибку в наборе строк, возвращенных **Execute** с помощью метода [инструкции](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) команды.  
  
```  
<return>  
   ...  
   <root>  
      ...  
      <CellData>  
      ...  
         <Cell CellOrdinal="10">  
            <Value>  
               <Error>  
                  <ErrorCode>2148497527</ErrorCode>   
                  <Description>Security Error.</Description>   
               </Error>  
            </Value>  
         </Cell>  
      </CellData>  
      ...  
   </root>  
   ...  
</return>  
```  
  
## <a name="see-also"></a>См. также  
 [Разработка с использованием XML для Аналитики в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

---
title: Обработка ошибок и предупреждений (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
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
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07b88d800237e5b4b06af0c1ff11cbd0af846600
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545021"
---
# <a name="handling-errors-and-warnings-xmla"></a>Обработка ошибок и предупреждений (XMLA)
  Обработка ошибок необходима, если вызов метода [обнаружения](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) или [выполнения](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) XML для аналитики (XMLA) не выполняется, выполняется успешно, но создает ошибки или предупреждения либо выполняется успешно, но возвращает результаты, содержащие ошибки.  
  
|Ошибка|Отчеты|  
|-----------|---------------|  
|Вызов метода XMLA не запускается|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращает сообщение об ошибке SOAP, содержащее сведения о сбое.<br /><br /> Дополнительные сведения см. в разделе [Обработка ошибок SOAP](#handling_soap_faults).|  
|Ошибки или предупреждения при успешном вызове метода|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]содержит элемент [Error](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) или [warning](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/warning-element-xmla) для каждой ошибки или предупреждения соответственно в свойстве [Messages](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla) [корневого](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) элемента, который содержит результаты вызова метода.<br /><br /> Дополнительные сведения см. в разделе [Обработка ошибок и предупреждений](#handling_errors_and_warnings).|  
|Ошибки в результате при успешном вызове метода|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]включает встроенный `error` `warning` элемент или для ошибки или предупреждения соответственно в соответствующую [ячейку](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) или элемент [Row](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/row-element-xmla) результатов вызова метода.<br /><br /> Дополнительные сведения см. в разделе [Обработка встроенных ошибок и предупреждений](#handling_inline_errors_and_warnings).|  
  
##  <a name="handling-soap-faults"></a><a name="handling_soap_faults"></a>Обработка ошибок SOAP  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращают сбой SOAP при возникновении следующих ситуаций.  
  
-   Сообщение SOAP, содержащее метод XMLA, имеет неправильный формат, или экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не может провести проверку его правильности.  
  
-   Произошла ошибка связи или другая ошибка, касающаяся сообщения SOAP, содержащего метод XMLA.  
  
-   Метод XMLA не запустился в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Коды сбоев SOAP для XMLA начинаются с «XMLForAnalysis», далее следуют точка и шестнадцатеричный код результата HRESULT. Например, код ошибки `0x80000005` форматируется как `XMLForAnalysis.0x80000005`. Дополнительные сведения о формате сбоев SOAP см. в разделе «Soap Fault» (Сбои Soap) документа «W3C Simple Object Access Protocol (SOAP) 1.1».  
  
### <a name="fault-code-information"></a>Сведения о кодах ошибок  
 В следующей таблице приведены сведения о кодах ошибок XMLA, которые содержатся в разделе подробностей ответа SOAP. Столбцы являются атрибутами ошибки в разделе подробностей сбоя SOAP.  
  
|Имя столбца|Тип|Описание|Допустимое значение NULL<sup>1</sup>|  
|-----------------|----------|-----------------|------------------------------|  
|`ErrorCode`|`UnsignedInt`|Код возврата, указывающий успешное или неудачное выполнение метода. Шестнадцатеричное значение необходимо преобразовать в значение `UnsignedInt`.|Нет|  
|`WarningCode`|`UnsignedInt`|Код возврата, указывающий состояние предупреждения. Шестнадцатеричное значение необходимо преобразовать в значение `UnsignedInt`.|Да|  
|`Description`|`String`|Текст ошибки или предупреждения и описание, возвращаемые компонентом, сформировавшим ошибку.|Да|  
|`Source`|`String`|Имя компонента, сформировавшего ошибку или предупреждение.|Да|  
|`HelpFile`|`String`|Путь или URL-адрес к файлу или разделу справки, в котором описывается ошибка или предупреждение.|Да|  
  
 <sup>1</sup> указывает, являются ли данные обязательными и должны ли они быть возвращены, а также данные являются необязательными, если столбец не применяется.  
  
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
  
##  <a name="handling-errors-and-warnings"></a><a name="handling_errors_and_warnings"></a>Обработка ошибок и предупреждений  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращают свойство `Messages` в элементе `root` для команды в случае возникновения следующих ситуаций после запуска этой команды.  
  
-   Сам метод выполнен успешно, но ошибка возникла в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] после успешного вызова метода.  
  
-   Экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращает предупреждение при успешном выполнении команды.  
  
 Свойство `Messages` следует за всеми остальными свойствами, содержащимися в элементе `root`; оно может содержать один или несколько элементов `Message`. В свою очередь, каждый элемент `Message` может содержать один из элементов `error` или `warning`, описывающий ошибки или предупреждения соответственно, возникшие в связи с указанной командой.  
  
 Дополнительные сведения об ошибках и предупреждениях, содержащихся в `Messages` свойстве, см. в разделе [messages &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla).  
  
### <a name="handling-errors-during-serialization"></a>Обработка ошибок во время сериализации  
 Если ошибка возникает после того, как [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляр уже начал сериализацию выходных данных успешно выполненной команды, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращает элемент [Exception](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/exception-element-xmla) в другом пространстве имен в момент возникновения ошибки. Затем экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] закрывает все открытые элементы с тем, чтобы XML-документ, отправляемый клиенту, был допустимым. Экземпляр возвращает также элемент `Messages`, содержащий описание ошибки.  
  
##  <a name="handling-inline-errors-and-warnings"></a><a name="handling_inline_errors_and_warnings"></a>Обработка встроенных ошибок и предупреждений  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращают встроенный элемент `error` или `warning` для команды, если сам метод XMLA выполнен успешно, а ошибка, характерная для элемента данных в результатах, возвращаемых методом, возникла в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] после успешного вызова метода XMLA.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]предоставляет встроенные `error` элементы и, `warning` Если возникают проблемы, связанные с ячейкой или другими данными, содержащимися в `root` элементе с использованием типа данных [MDDataSet](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/mddataset-data-type-xmla) , например ошибка безопасности или ошибка форматирования для ячейки. В этих случаях службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращают элемент `error` или `warning` в элементе `Cell` или `row`, который содержит ошибку или предупреждение соответственно.  
  
 В следующем примере показан результирующий набор, содержащий ошибку в наборе строк, возвращенном из `Execute` метода с помощью команды [инструкции](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) .  
  
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
  
## <a name="see-also"></a>См. также:  
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  

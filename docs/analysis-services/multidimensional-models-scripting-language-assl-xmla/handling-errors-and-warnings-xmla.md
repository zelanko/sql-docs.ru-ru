---
title: Обработка ошибок и предупреждений (XMLA) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 884474398abc9f449e5f6bd82c9f4b981f9a3a43
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63261695"
---
# <a name="handling-errors-and-warnings-xmla"></a>Обработка ошибок и предупреждений (XMLA)
  Обработка ошибок является обязательным, если XML для аналитики (XMLA) [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) или [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) вызов метода не выполняется, выполняется успешно, но создает ошибки или предупреждения, или выполняется успешно, но возвращает результаты содержащие ошибки.  
  
|Ошибка|Отчет|  
|-----------|---------------|  
|Вызов метода XMLA не запускается|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Возвращает сообщение о сбое SOAP, содержащий сведения об ошибке.<br /><br /> Дополнительные сведения см. разделе [обработка сбоев SOAP](#handling_soap_faults).|  
|Ошибки или предупреждения при успешном вызове метода|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] включает в себя [ошибка](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) или [предупреждение](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/warning-element-xmla) -элемент для каждой ошибки или предупреждения, соответственно, в [сообщений](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla) свойство [корневой](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) элемент содержащий результаты вызова метода.<br /><br /> Дополнительные сведения см. разделе [обработка ошибок и предупреждений](#handling_errors_and_warnings).|  
|Ошибки в результате при успешном вызове метода|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] включает в себя встроенный **ошибка** или **предупреждение** элемент для ошибки или предупреждения, соответственно в предназначенный [ячейки](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) или [строки](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/row-element-xmla) элемент результаты вызова метода.<br /><br /> Дополнительные сведения см. разделе [обработка встроенных ошибок и предупреждений](#handling_inline_errors_and_warnings).|  
  
##  <a name="handling_soap_faults"></a> Обработка сбоев SOAP  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращают сбой SOAP при возникновении следующих ситуаций.  
  
-   Сообщение SOAP, содержащее метод XMLA, имеет неправильный формат, или экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не может провести проверку его правильности.  
  
-   Произошла ошибка связи или другая ошибка, касающаяся сообщения SOAP, содержащего метод XMLA.  
  
-   Метод XMLA не запустился в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Коды сбоев SOAP для XMLA начинаются с «XMLForAnalysis», далее следуют точка и шестнадцатеричный код результата HRESULT. Например, код ошибки `0x80000005` форматируется как `XMLForAnalysis.0x80000005`. Дополнительные сведения о формате сбоев SOAP см. в разделе «Soap Fault» (Сбои Soap) документа «W3C Simple Object Access Protocol (SOAP) 1.1».  
  
### <a name="fault-code-information"></a>Сведения о кодах ошибок  
 В следующей таблице приведены сведения о кодах ошибок XMLA, которые содержатся в разделе подробностей ответа SOAP. Столбцы являются атрибутами ошибки в разделе подробностей сбоя SOAP.  
  
|Имя столбца|Тип|Описание|Значение NULL разрешено<sup>1</sup>|  
|-----------------|----------|-----------------|------------------------------|  
|**ErrorCode**|**UnsignedInt**|Код возврата, указывающий успешное или неудачное выполнение метода. Шестнадцатеричное значение необходимо преобразовать в **UnsignedInt** значение.|Нет|  
|**WarningCode**|**UnsignedInt**|Код возврата, указывающий состояние предупреждения. Шестнадцатеричное значение необходимо преобразовать в **UnsignedInt** значение.|Да|  
|**Описание**|**String**|Текст ошибки или предупреждения и описание, возвращаемые компонентом, сформировавшим ошибку.|Да|  
|**Source**|**String**|Имя компонента, сформировавшего ошибку или предупреждение.|Да|  
|**HelpFile**|**String**|Путь или URL-адрес к файлу или разделу справки, в котором описывается ошибка или предупреждение.|Да|  
  
 <sup>1</sup> указывает ли данные является обязательным и должен быть возвращен, или ли данные является необязательным и допустима пустая строка, если столбец не применяется.  
  
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
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Возвращает **сообщений** свойство в **корневой** элемента для команды в случае возникновения следующих ситуаций после запуска этой команды:  
  
-   Сам метод выполнен успешно, но ошибка возникла в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] после успешного вызова метода.  
  
-   Экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращает предупреждение при успешном выполнении команды.  
  
 **Сообщений** свойство следует за все остальные свойства, содержащиеся в **корневой** элемент и может содержать один или несколько **сообщение** элементов. В свою очередь, каждый **сообщение** элемент может содержать один **ошибка** или **предупреждение** элемент, описывающий ошибки или предупреждения, соответственно, произошло Указанная команда.  
  
 Дополнительные сведения об ошибках и предупреждениях, содержащихся в **сообщений** свойство, см. в разделе [элемент Messages &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla).  
  
### <a name="handling-errors-during-serialization"></a>Обработка ошибок во время сериализации  
 Если ошибка возникает после [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляр уже начал сериализацию выходных данных успешно выполненной команды, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращает [исключение](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/exception-element-xmla) элемент в другом пространстве имен точке ошибки. Затем экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] закрывает все открытые элементы с тем, чтобы XML-документ, отправляемый клиенту, был допустимым. Экземпляр возвращает также **сообщений** элемент, содержащий описание ошибки.  
  
##  <a name="handling_inline_errors_and_warnings"></a> Обработка встроенных ошибок и предупреждений  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Возвращает встроенную **ошибка** или **предупреждение** для команды, если сам метод XMLA выполнен, но произошла ошибка, характерная для элемента данных в результатах, возвращаемых методом на [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляр после успешного вызова метода XMLA.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставляет встроенные **ошибка** и **предупреждение** элементов, если проблем, характерных для ячейки или с другими данными, которые содержатся в **корневой** элемента с помощью [ MDDataSet](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/mddataset-data-type-xmla) применяемый тип данных, таких как ошибка безопасности или ошибка форматирования для ячейки. В этих случаях [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращает **ошибка** или **предупреждение** элемент в **ячейки** или **строки** элемент, который содержит ошибку или Предупреждение "," соответственно.  
  
 В следующем примере показан результирующий набор, который содержит ошибку в наборе строк, возвращаемых из **Execute** с помощью метода [инструкции](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) команды.  
  
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
 [Разработка с использованием XMLA в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

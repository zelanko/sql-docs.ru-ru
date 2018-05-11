---
title: Создание и изменение объектов (XMLA) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2c43b95e68f25527e26eac54f5e44366edf39117
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="creating-and-altering-objects-xmla"></a>Создание и изменение объектов (XMLA)
  Основные объекты можно создавать, изменять и удалять независимо. Основные объекты включают следующие объекты:  
  
-   Серверы  
  
-   Базы данных  
  
-   Измерения  
  
-   Кубы  
  
-   Группы мер  
  
-   Секции  
  
-   Перспективы  
  
-   Модели интеллектуального анализа данных  
  
-   Роли  
  
-   Команды, связанные с сервером или базой данных  
  
-   Источники данных  
  
 Вы используете [создать](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md) команду, чтобы создать основной объект в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]и [Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) для изменения основного объекта, существующего в экземпляре. Обе команды запускаются с помощью [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) метод.  
  
## <a name="creating-objects"></a>Создание объектов  
 При создании объектов с помощью **создать** метод, необходимо сначала определить родительский объект, содержащий [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] создаваемого объекта. Родительский объект определяется путем указания ссылки объекта в [ParentObject](../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md) свойство **создать** команды. Каждая ссылка объекта содержит идентификаторы объекта, необходимые для уникальной идентификации родительский объект для **создать** команды. Дополнительные сведения о ссылках на объекты см. в разделе [определение и идентификация объектов &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md).  
  
 Например, следует указать ссылку объекта на куб, чтобы создать новую группу мер для этого куба. Ссылка на объект для куба в **ParentObject** свойство содержит идентификатор базы данных и идентификатор куба, как тот же идентификатор куба может быть использована потенциально на другую базу данных.  
  
 [ObjectDefinition](../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md) содержатся элементы языка сценариев служб Analysis Services (ASSL), определяющие основной объект должен быть создан. Дополнительные сведения о ASSL см. в разделе [разработки в язык сценариев служб Analysis Services &#40;ASSL&#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Если задать **AllowOverwrite** атрибут **создать** команды значение true, можно переписать существующий основной объект, имеющий указанный идентификатор. В противном случае, если основной объект с указанным идентификатором уже существует в родительском объекте, возникает ошибка.  
  
 Дополнительные сведения о **создать** см. в разделе [Создание элемента &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md).  
  
### <a name="creating-session-objects"></a>Создание объектов сеанса  
 Объекты сеанса — это временные объекты, доступные только для явных или неявных сеансов, которые используются клиентским приложением и удаляются по завершении сеанса. Можно создать объекты сеанса, присвоив **область** атрибут **создать** команды *сеанса*.  
  
> [!NOTE]  
>  При использовании *сеанса* параметр **ObjectDefinition** элемент может содержать только [измерения](../../analysis-services/scripting/objects/dimension-element-assl.md), [куба](../../analysis-services/scripting/objects/cube-element-assl.md), или [ MiningModel](../../analysis-services/scripting/objects/miningmodel-element-assl.md) элементы языка ASSL.  
  
## <a name="altering-objects"></a>Изменение объектов  
 При изменении объектов с помощью **Alter** метод, сначала нужно определить объект для изменения, указав ссылку на объект в [объекта](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) свойство **Alter**команды. Каждая ссылка объекта содержит идентификаторы объекта, необходимые для уникальной идентификации объекта для **Alter** команды. Дополнительные сведения о ссылках на объекты см. в разделе [определение и идентификация объектов &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md).  
  
 Например, чтобы изменить структуру куба, необходимо указать ссылку объекта на куб. Ссылка на объект для куба в **объекта** свойство содержит идентификатор базы данных и идентификатор куба, как тот же идентификатор куба может быть использована потенциально на другую базу данных.  
  
 **ObjectDefinition** элемент содержит элементы ASSL, определяющие основной объект для изменения. Дополнительные сведения о ASSL см. в разделе [разработки в язык сценариев служб Analysis Services &#40;ASSL&#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Если задать **AllowCreate** атрибут **Alter** команды значение true, если объект не существует, можно создать указанный основной объект. В противном случае, если указанный основной объект еще не существует, возникает ошибка.  
  
### <a name="using-the-objectexpansion-attribute"></a>Использование атрибута ObjectExpansion  
 Если вы меняете только свойства основного объекта и без переопределения второстепенных объектов, содержащихся в основном объекте, можно установить **ObjectExpansion** атрибут **Alter** команды *ObjectProperties*. **ObjectDefinition** свойство затем должно содержать только элементы для свойств основного объекта и **Alter** оставляет второстепенные объекты, связанные с основным объектом, без изменений.  
  
 Чтобы переопределить второстепенные объекты для основного объекта, необходимо задать **ObjectExpansion** атрибут *ExpandFull* и определение объекта должны включать все второстепенные объекты, содержащиеся в основном объекте. Если **ObjectDefinition** свойство **Alter** команда не включает явно второстепенный объект, содержащийся в основном объекте, удаляется второстепенный объект, который не был включен.  
  
### <a name="altering-session-objects"></a>Изменение объектов сеанса  
 Чтобы изменить объекты сеанса, созданные **создать** команды, задайте **область** атрибут **Alter** команды *сеанса*.  
  
> [!NOTE]  
>  При использовании *сеанса* параметр **ObjectDefinition** элемент может содержать только [измерения](../../analysis-services/scripting/objects/dimension-element-assl.md), [куба](../../analysis-services/scripting/objects/cube-element-assl.md), или [ MiningModel](../../analysis-services/scripting/objects/miningmodel-element-assl.md) элементы языка ASSL.  
  
## <a name="creating-or-altering-subordinate-objects"></a>Создание или изменение подчиненных объектов  
 Несмотря на то что **создать** или **Alter** команда создает или изменяет только один самый верхний основной объект, создаваемый или изменяемый основной объект может содержать определения во включающем  **ObjectDefinition** свойств для других основные и второстепенные объекты, которые ему подчинены. Например, при определении куба, указать родительскую базу данных в **ParentObject**и в пределах определения куба в **ObjectDefinition** можно определить группы мер для куба, а также в меру группы можно определить секции для каждой группы мер. Второстепенный объект можно определить только в содержащем его основном объекте. Дополнительные сведения об основных и второстепенных объектах см. в разделе [объектов базы данных &#40;службы Analysis Services — многомерные данные&#41;](../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="description"></a>Описание  
 В следующем примере создается источника реляционных данных, который ссылается на [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] пример [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных.  
  
### <a name="code"></a>код  
  
```  
<Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    </ParentObject>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=localhost;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ImpersonationInfo>  
                <ImpersonationMode>ImpersonateServiceAccount</ImpersonationMode>  
            </ImpersonationInfo>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT0S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Create>  
```  
  
### <a name="description"></a>Описание  
 В следующем примере реляционный источник данных, созданный в предыдущем примере, изменяется путем задания времени ожидания запроса для источника данных, равного 30 секундам.  
  
### <a name="code"></a>код  
  
```  
<Alter ObjectExpansion="ObjectProperties" xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DataSourceID>AdventureWorksDW2012</DataSourceID>  
    </Object>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=fr-dwk-02;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT30S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Alter>  
```  
  
### <a name="comments"></a>Комментарии  
 **ObjectExpansion** атрибут **Alter** команды было задано значение *ObjectProperties*. Этот параметр позволяет [ImpersonationInfo](../../analysis-services/scripting/properties/impersonationinfo-element-assl.md) элемент, второстепенный объект, который необходимо исключить из источника данных, определенного в **ObjectDefinition**. Поэтому в качестве данных об олицетворении для этого источника данных остается заданной учетная запись службы, как указано в первом примере.  
  
## <a name="see-also"></a>См. также  
 [Метод Execute &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)   
 [Развертывание с помощью функций анализа служб языка сценариев &#40;ASSL&#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Разработка с использованием XML для Аналитики в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

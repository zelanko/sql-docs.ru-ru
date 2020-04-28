---
title: Создание и изменение объектов (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- subordinate objects [XML for Analysis]
- XML for Analysis, objects
- modifying objects
- removing objects
- deleting objects
- XMLA, objects
ms.assetid: a2080867-e130-440c-92eb-f768869f34a8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3dcc6eedc97b3d476d79420b4e067883e17f03d2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62702301"
---
# <a name="creating-and-altering-objects-xmla"></a>Создание и изменение объектов (XMLA)
  Основные объекты можно создавать, изменять и удалять независимо. Основные объекты включают следующие объекты:  
  
-   Серверы  
  
-   Базы данных  
  
-   Измерения  
  
-   Кубы  
  
-   Группы мер  
  
-   Секции  
  
-   перспективами  
  
-   Модели интеллектуального анализа данных  
  
-   Роли  
  
-   Команды, связанные с сервером или базой данных  
  
-   Источники данных  
  
 Команда [CREATE](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) используется для создания основного объекта в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]служб, а команда [ALTER](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) — для изменения существующего основного объекта в экземпляре. Обе команды выполняются с помощью метода [EXECUTE](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) .  
  
## <a name="creating-objects"></a>Создание объектов  
 Объекты можно создавать при помощи метода `Create`; для этого сначала необходимо определить родительский объект, содержащий объект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], который должен быть создан. Вы определяете родительский объект, предоставив ссылку на объект в свойстве [ParentObject](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) `Create` команды. Каждая ссылка объекта содержит идентификаторы объекта, необходимые, чтобы идентифицировать родительский объект для команды `Create` уникальным образом. Дополнительные сведения о ссылках на объекты см. в разделе [Определение и идентификация объектов &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).  
  
 Например, следует указать ссылку объекта на куб, чтобы создать новую группу мер для этого куба. Ссылка на объект для куба в свойстве `ParentObject` содержит идентификатор базы данных и идентификатор куба, поскольку тот же идентификатор куба может использоваться в другой базе данных.  
  
 Элемент [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) содержит Analysis Services элементы языка ASSL, определяющие основной объект, который необходимо создать. Дополнительные сведения о языке ASSL см. в разделе [Разработка с использованием Analysis Services языка сценариев &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Если атрибуту `AllowOverwrite` команды `Create` задать значение TRUE, можно переписать существующий основной объект, имеющий указанный идентификатор. В противном случае, если основной объект с указанным идентификатором уже существует в родительском объекте, возникает ошибка.  
  
 Дополнительные сведения о команде см `Create` . в разделе [Создание элемента &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla).  
  
### <a name="creating-session-objects"></a>Создание объектов сеанса  
 Объекты сеанса — это временные объекты, доступные только для явных или неявных сеансов, которые используются клиентским приложением и удаляются по завершении сеанса. Вы можете создавать объекты сеанса, присвоив `Scope` атрибуту `Create` команды значение *Session*.  
  
> [!NOTE]  
>  При использовании параметра *сеанса* `ObjectDefinition` элемент может содержать только [измерения](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [Кубы](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)или [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) элементы ASSL.  
  
## <a name="altering-objects"></a>Изменение объектов  
 При изменении объектов с помощью `Alter` метода необходимо сначала указать объект, который необходимо изменить, предоставив ссылку на объект в свойстве [объекта](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) `Alter` команды. Каждая ссылка объекта содержит идентификаторы объекта, необходимые, чтобы уникальным образом идентифицировать объект для команды `Alter`. Дополнительные сведения о ссылках на объекты см. в разделе [Определение и идентификация объектов &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).  
  
 Например, чтобы изменить структуру куба, необходимо указать ссылку объекта на куб. Ссылка на объект для куба в свойстве `Object` содержит идентификатор базы данных и идентификатор куба, поскольку тот же идентификатор куба может использоваться в другой базе данных.  
  
 Элемент `ObjectDefinition` содержит элементы языка ASSL, определяющие основной объект, которые должен быть изменен. Дополнительные сведения о языке ASSL см. в разделе [Разработка с использованием Analysis Services языка сценариев &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Если атрибуту `AllowCreate` команды `Alter` задать значение TRUE, можно создать указанный основной объект, если он не существует. В противном случае, если указанный основной объект еще не существует, возникает ошибка.  
  
### <a name="using-the-objectexpansion-attribute"></a>Использование атрибута ObjectExpansion  
 Если изменяются только свойства основного объекта и не переопределяются небольшие объекты, содержащиеся в основном объекте, можно установить `ObjectExpansion` атрибут `Alter` команды *ObjectProperties*. В этом случае свойство `ObjectDefinition` должно содержать только элементы для свойств основного объекта, а команда `Alter` оставляет второстепенные объекты, ассоциированные с основным объектом, без изменений.  
  
 Чтобы переопределить незначительные объекты для основного объекта, необходимо задать для `ObjectExpansion` атрибута значение *ExpandFull* , а определение объекта должно включать все небольшие объекты, содержащиеся в основном объекте. Если в свойство `ObjectDefinition` команды `Alter` явно не включен второстепенный объект, содержащийся в основном объекте, то не указанный в нем второстепенный объект удаляется.  
  
### <a name="altering-session-objects"></a>Изменение объектов сеанса  
 Чтобы изменить `Create` объекты сеанса, созданные командой, присвойте `Scope` атрибуту `Alter` команды значение *Session*.  
  
> [!NOTE]  
>  При использовании параметра *сеанса* `ObjectDefinition` элемент может содержать только [измерения](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [Кубы](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)или [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) элементы ASSL.  
  
## <a name="creating-or-altering-subordinate-objects"></a>Создание или изменение подчиненных объектов  
 Хотя команда `Create` или `Alter` создает или изменяет только один самый верхний основной объект, создаваемый или изменяемый основной объект может содержать во включающем свойстве `ObjectDefinition` определения для других основных или второстепенных объектов, которые ему подчинены. Например, при определении куба родительская база данных указывается в свойстве `ParentObject`, тогда как в рамках определения куба в свойстве `ObjectDefinition` можно определить группы мер для куба, а в рамках групп мер — определить секции для каждой группы мер. Второстепенный объект можно определить только в содержащем его основном объекте. Дополнительные сведения о основных и вспомогательных объектах см. в разделе [Database objects &#40;Analysis Services многомерных данных&#41;](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="description"></a>Описание  
 В следующем примере создается реляционный источник данных, ссылающийся на [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] образец [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных.  
  
### <a name="code"></a>Код  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
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
  
### <a name="code"></a>Код  
  
```  
<Alter ObjectExpansion="ObjectProperties" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
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
 `ObjectExpansion` Атрибуту `Alter` команды было присвоено значение *ObjectProperties*. Этот параметр позволяет исключить элемент [ImpersonationInfo](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl) , дополнительный объект, из источника данных, определенного в `ObjectDefinition`. Поэтому в качестве данных об олицетворении для этого источника данных остается заданной учетная запись службы, как указано в первом примере.  
  
## <a name="see-also"></a>См. также  
 [Метод Execute &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)   
 [Разработка с помощью Analysis Services языка сценариев &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  

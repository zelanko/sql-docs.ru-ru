---
title: Выполнение пакетных операций (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- multiple projects
- XML for Analysis, batches
- parallel batch execution [XMLA]
- transactional batches
- serial batch execution [XMLA]
- XMLA, batches
- batches [XML for Analysis]
- nontransactional batches
ms.assetid: 731c70e5-ed51-46de-bb69-cbf5aea18dda
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2bd661506dbb792eb55194c61d7284d619e63a5f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62702065"
---
# <a name="performing-batch-operations-xmla"></a>Выполнение пакетных операций (XMLA)
  Можно использовать [пакета](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) в XML для аналитики (XMLA) для выполнения нескольких команд XMLA при помощи только одного команда [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) метод. Несколько команд, содержащихся в команде `Batch`, можно выполнить либо как одну транзакцию, либо как отдельные транзакции для каждой команды, последовательно или параллельно. Можно также указать out-привязок и другие свойства в `Batch` команды для обработки нескольких [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объектов.  
  
## <a name="running-transactional-and-nontransactional-batch-commands"></a>Выполнение транзакционных и нетранзакционных пакетных команд  
 Команда `Batch` выполняет команды одним из двух способов.  
  
 **Транзакционная**  
 Если `Transaction` атрибут `Batch` команды установлено значение true, `Batch` команда выполняет все команды, содержащиеся `Batch` команды в рамках одной транзакции в *транзакций* пакетной службы.  
  
 При сбое любой команды в пакете транзакций [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] откат всех команд `Batch` команда, были выполнены до команды, завершившейся неудачей и `Batch` команда немедленно завершается. Все команды, содержащиеся в команде `Batch`, которые еще не запускались, выполняться не будут. После завершения команды `Batch` команда `Batch` сообщает обо всех ошибках, возникших при выполнении команды, завершившейся неудачей.  
  
 **Nontransactional**  
 Если `Transaction` атрибут имеет значение false, `Batch` команда выполняет каждую команду, содержащуюся `Batch` команду в отдельной транзакции a *нетранзакционные* пакетной службы. Если в нетранзакционном пакете одна из команд завершается ошибкой, команда `Batch` продолжает выполнение команд после той команды, которая завершилась неудачей. После того как команда `Batch` предпримет попытки выполнить все команды, содержащиеся в команде `Batch`, то команда `Batch` сообщит обо всех возникших ошибках.  
  
 Все результаты, возвращаемые командами, которые содержатся в команде `Batch`, возвращаются в том порядке, в котором эти команды расположены в команде `Batch`. В зависимости от того, является ли команда `Batch` транзакционной или нетранзакционной, команда `Batch` возвращает разные результаты.  
  
> [!NOTE]  
>  Если `Batch` команд содержит команду, которая не возвращает выходные данные, такие как [блокировки](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) команда, и что команда выполнена успешно, `Batch` команда возвращает пустой [корневой](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) элемент в элементе результатов. Пустой элемент `root` дает возможность сопоставить каждую команду, содержащуюся в команде `Batch`, с соответствующим элементом `root` для результатов этой команды.  
  
### <a name="returning-results-from-transactional-batch-results"></a>Возвращение результатов из результатов транзакционного пакета  
 Результаты команд, выполняющихся в рамках транзакционного пакета, возвращаются только после завершения выполнения всей команды `Batch`. Результаты каждой команды не возвращаются отдельно по мере их выполнения, поскольку завершение с ошибкой любой команды в рамках транзакционного пакета приводит к откату всей команды `Batch` и всех содержащихся в ней команд. Если все команды запустились и выполнены успешно, [возвращают](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/return-element-xmla) элемент [ExecuteResponse](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects-executeresponse) элемент, возвращаемый `Execute` метод `Batch` команды содержит одно [результатов](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/results-element-xmla) элемент, который в свою очередь содержит один `root` -элемент для каждой успешно выполненной команды, содержащиеся в `Batch` команды. Если же одну из команд в команде `Batch` не удалось запустить или она завершилась ошибкой, метод `Execute` возвращает сбой SOAP для команды `Batch`, в котором содержится ошибка команды, завершившейся неудачей.  
  
### <a name="returning-results-from-nontransactional-batch-results"></a>Возвращение результатов из результатов нетранзакционного пакета  
 Результаты выполнения команд в рамках нетранзакционного пакета возвращаются в том порядке, в котором эти команды расположены в команде `Batch` и с учетом их возврата каждой командой. Если не удалось запустить ни одной команды, содержащейся в команде `Batch`, метод `Execute` возвращает сбой SOAP, который содержит ошибку для команды `Batch`. Если удалось запустить хотя бы одну команду, элемент `return` элемента `ExecuteResponse`, возвращаемого методом `Execute` для команды `Batch`, будет содержать один элемент `results`, в котором, в свою очередь, будет содержаться по одному элементу `root` для каждой команды, находящейся в команде `Batch`. Если одной или нескольких команд в рамках нетранзакционного пакета не может быть запущена или не удается завершить, `root` содержит элемент для завершившейся неудачно команды [ошибка](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) элемент, описывающий ошибку.  
  
> [!NOTE]  
>  Считается, что нетранзакционный пакет выполнен успешно, если из него удалось запустить хотя бы одну команду, даже если все команды, содержащиеся в таком пакете, возвратят ошибку в результатах выполнения команды `Batch`.  
  
## <a name="using-serial-and-parallel-execution"></a>Использование последовательного и параллельного выполнения  
 Команду `Batch` можно использовать для последовательного или параллельного выполнения включенных в нее команд. При последовательном выполнении следующая команда из команды `Batch` может запуститься только после завершения выполнения текущей команды в команде `Batch`. При параллельном выполнении команд команда `Batch` может выполнять несколько команд одновременно.  
  
 Для выполнения команд в параллельном режиме, необходимо добавить команды, должны выполняться в параллельном режиме в [параллельных](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/parallel-element-xmla) свойство `Batch` команды. В настоящее время [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно запустить только непрерывные, последовательные [процесс](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) команды в параллельном режиме. Любые другие команды XMLA, такие как [создать](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) или [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla), входящий в `Parallel` свойство, выполняются последовательно.  
  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] пытаются выполнить все команды `Process`, включенные в свойство `Parallel`, в параллельном режиме, однако гарантировать параллельное выполнение всех команд `Process` невозможно. Экземпляр анализирует каждую команду `Process`, а если обнаруживается, что выполнить команду в параллельном режиме невозможно, выполняет команду `Process` последовательно.  
  
> [!NOTE]  
>  Чтобы команды можно было выполнять параллельно, атрибуту `Transaction` команды `Batch` необходимо присвоить значение TRUE, так как службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают только одну активную транзакцию на соединение, а нетранзакционные пакеты выполняют каждую команду в отдельной транзакции. В случае включения свойства `Parallel` в нетранзакционный пакет возникнет ошибка.  
  
### <a name="limiting-parallel-execution"></a>Ограничение параллельного выполнения  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] пытаются выполнить как можно большее число команд `Process` параллельно, с учетом возможностей компьютера, на котором работает экземпляр служб. Можно ограничить число одновременно выполняющихся команд `Process`, присвоив атрибуту `maxParallel` свойства `Parallel` значение, указывающее максимальное число команд `Process`, которые могут выполняться параллельно.  
  
 Например, в приведенной последовательности свойство `Parallel` содержит следующие команды:  
  
1.  `Create`  
  
2.  `Process`  
  
3.  `Alter`  
  
4.  `Process`  
  
5.  `Process`  
  
6.  `Process`  
  
7.  `Delete`  
  
8.  `Process`  
  
9. `Process`  
  
 Атрибут `maxParalle` этого свойства `Parallel` имеет значение 2. Это означает, что экземпляр выполнит приведенный ранее список команд в следующем порядке.  
  
-   Команда 1 будет выполнена последовательно, так как это команда `Create`, а параллельно могут выполняться только команды `Process`.  
  
-   Команда 2 выполняется последовательно после завершения команды 1.  
  
-   Команда 3 выполняется последовательно после завершения команды 2.  
  
-   Команды, 4 и 5 выполняются в параллельном режиме, после завершения команды 3. Несмотря на то, что команда 6 также является командой `Process`, она не может выполняться параллельно с командами 4 и 5, поскольку свойство `maxParallel` имеет значение 2.  
  
-   Команда будет выполнена последовательно после завершения команд 4 и 5.  
  
-   Команда 7 выполняется последовательно за командой 6.  
  
-   Команды 8 и 9 выполняются параллельно после завершения команды 7.  
  
## <a name="using-the-batch-command-to-process-objects"></a>Использование пакетов команд для обработки объектов  
 Команда `Batch` содержит несколько дополнительных свойств и атрибутов, включенных в нее специально для поддержки обработки нескольких проектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
-   Атрибут `ProcessAffectedObjects` команды `Batch` указывает, должен ли экземпляр обрабатывать также любые объекты, которым в результате команды `Process`, включенной в команду `Batch`, обрабатывающую указанный объект, требуется повторная обработка.  
  
-   [Привязки](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla) свойство содержит коллекцию привязок вне строки, используемые всеми `Process` команды в `Batch` команды.  
  
-   [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) содержит привязку вне строки для источника данных, используемые всеми `Process` команды в `Batch` команды.  
  
-   [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) содержит привязку вне строки для представления источников данных, используемые всеми `Process` команды в `Batch` команды.  
  
-   [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) указывает то, как в котором `Batch` команда обрабатывает ошибки, обнаруженные всеми `Process` команд, содержащихся в `Batch` команду.  
  
    > [!IMPORTANT]  
    >  Команда `Process` не может содержать свойств `Bindings`, `DataSource`, `DataSourceView`, `ErrorConfiguration` или `Process`, если она находится в команде `Batch`. Если эти свойства для команды `Process` задать необходимо, укажите требуемые сведения в соответствующих свойствах команды `Batch`, которая содержит команду `Process`.  
  
## <a name="see-also"></a>См. также  
 [Элемент Batch &#40;XML для Аналитики&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)   
 [Обработать элемент &#40;XML для Аналитики&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)   
 [Обработка объектов многомерной модели](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  

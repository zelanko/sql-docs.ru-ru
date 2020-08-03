---
title: API расширяемости
description: Узнайте об API расширяемости Azure Data Studio, с помощью которых расширения могут взаимодействовать с другими компонентами Azure Data Studio (например обозревателем объектов).
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 0ef95d4b77e91bcd950b2d8aa5dddf5bb95b3841
ms.sourcegitcommit: 620a868e623134ad6ced6728ce9d03d7d0038fe0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87411140"
---
# <a name="azure-data-studio-extensibility-apis"></a>Интерфейсы API расширяемости Azure Data Studio

Azure Data Studio предоставляет интерфейсы API, с помощью которых расширения могут взаимодействовать с другими компонентами Azure Data Studio, такими как обозреватель объектов. Эти интерфейсы API доступны в файле [`src/sql/azdata.d.ts`](https://github.com/Microsoft/azuredatastudio/blob/main/src/sql/azdata.d.ts) и описываются ниже.

## <a name="connection-management"></a>Управление подключениями
`azdata.connection`

### <a name="top-level-functions"></a>Общие функции

- `getCurrentConnection(): Thenable<azdata.connection.Connection>` — возвращает текущее подключение в соответствии с активным выбором в редакторе или обозревателе объектов.

- `getActiveConnections(): Thenable<azdata.connection.Connection[]>` — возвращает список всех активных подключений пользователя. Если таких подключений нет, возвращается пустой список.

- `getCredentials(connectionId: string): Thenable<{ [name: string]: string }>` — возвращает словарь, который содержит учетные данные, связанные с подключением. Они также возвращаются в словаре параметров в объекте `azdata.connection.Connection`, но при использовании данной функции они удаляются из этого объекта. 

### `Connection`
- `options: { [name: string]: string }` — словарь параметров подключения.
- `providerName: string` — имя поставщика подключений (например, "MSSQL").
- `connectionId: string` — уникальный идентификатор подключения.

### <a name="example-code"></a>Пример кода
```
> let connection = azdata.connection.getCurrentConnection();
connection: {
    providerName: 'MSSQL',
    connectionId: 'd97bb63a-466e-4ef0-ab6f-00cd44721dcc',
    options: {
        server: 'mairvine-sql-server',
        user: 'sa',
        authenticationType: 'sqlLogin',
        ...
    },
    ...
}
> let credentials = azdata.connection.getCredentials(connection.connectionId);
credentials: {
    password: 'abc123'
}

```

## <a name="object-explorer"></a>Обозреватель объектов

`azdata.objectexplorer`


### <a name="top-level-functions"></a>Общие функции
- `getNode(connectionId: string, nodePath?: string): Thenable<azdata.objectexplorer.ObjectExplorerNode>` — возвращает узел обозревателя объектов, соответствующий данному подключению и пути. Если путь не указан, возвращается узел верхнего уровня для данного подключения. Если по указанному пути нет узла, возвращается значение `undefined`. Примечание. Значение `nodePath` для объекта создается сервером службы средств SQL; составить его вручную сложно. В будущем с помощью API можно будет получать узлы на основе предоставленных метаданных, таких как имя, тип и схема узла.

- `getActiveConnectionNodes(): Thenable<azdata.objectexplorer.ObjectExplorerNode>` — возвращает все активные узлы подключений в обозревателе объектов.

- `findNodes(connectionId: string, type: string, schema: string, name: string, database: string, parentObjectNames: string[]): Thenable<azdata.objectexplorer.ObjectExplorerNode[]>` — поиск всех узлов обозревателя объектов, соответствующих указанным метаданным. Аргументы `schema`, `database` и `parentObjectNames` должны иметь значение `undefined`, если они не применимы. `parentObjectNames` — это список родительских объектов, отличных от баз данных, для нужного объекта от самого высокого до самого низкого уровня в обозревателе объектов. Например, для поиска столбца "column1", относящегося к таблице "schema1.table1" и базе данных "database1" с идентификатором подключения `connectionId`, выполните вызов `findNodes(connectionId, 'Column', undefined, 'column1', 'database1', ['schema1.table1'])`. Кроме того, см. [список типов, поддерживаемых по умолчанию в Azure Data Studio](https://github.com/Microsoft/azuredatastudio/wiki/Object-Explorer-types-supported-by-FindNodes-API) для этого вызова API.

### <a name="objectexplorernode"></a>ObjectExplorerNode
- `connectionId: string` — идентификатор подключения, к которому относится узел.

- `nodePath: string` — путь к узлу, используемый для вызова функции `getNode`.

- `nodeType: string` — строка, представляющая тип узла.

- `nodeSubType: string` — строка, представляющая подтип узла.

- `nodeStatus: string` — строка, представляющая состояние узла.

- `label: string` — метка узла, отображаемая в обозревателе объектов.

- `isLeaf: boolean` — является ли узел листовым, то есть не имеет дочерних узлов.

- `metadata: azdata.ObjectMetadata` — метаданные, которые описывают объект, представленный этим узлом.

- `errorMessage: string` — сообщение, которое выводится, если узел находится в состоянии ошибки.

- `isExpanded(): Thenable<boolean>` — развернут ли узел в обозревателе объектов в настоящее время.

- `setExpandedState(expandedState: vscode.TreeItemCollapsibleState): Thenable<void>` — развертывание или свертывание узла. Если задается значение None, состояние узла не меняется.

- `setSelected(selected: boolean, clearOtherSelections?: boolean): Thenable<void>` — задает состояние выбора узла. Если `clearOtherSelections` имеет значение true, при новом выборе текущий выбор отменяется. Если задано значение false, текущий выбор сохраняется. `clearOtherSelections` по умолчанию имеет значение true, если `selected` имеет значение true, и false, если `selected` имеет значение false.

- `getChildren(): Thenable<azdata.objectexplorer.ObjectExplorerNode[]>` — возвращает все дочерние узлы этого узла. Если дочерних узлов нет, возвращается пустой список.

- `getParent(): Thenable<azdata.objectexplorer.ObjectExplorerNode>` — возвращает родительский узел этого узла. При отсутствии родительского узла возвращается значение undefined.

### <a name="example-code"></a>Пример кода

```cs
private async interactWithOENode(selectedNode: azdata.objectexplorer.ObjectExplorerNode): Promise<void> {
    let choices = ['Expand', 'Collapse', 'Select', 'Select (multi)', 'Deselect', 'Deselect (multi)'];
    if (selectedNode.isLeaf) {
        choices[0] += ' (is leaf)';
        choices[1] += ' (is leaf)';
    } else {
        let expanded = await selectedNode.isExpanded();
        if (expanded) {
            choices[0] += ' (is expanded)';
        } else {
            choices[1] += ' (is collapsed)';
        }
    }
    let parent = await selectedNode.getParent();
    if (parent) {
        choices.push('Get Parent');
    }
    let children = await selectedNode.getChildren();
    children.forEach(child => choices.push(child.label));
    let choice = await vscode.window.showQuickPick(choices);
    let nextNode: azdata.objectexplorer.ObjectExplorerNode = undefined;
    if (choice === choices[0]) {
        selectedNode.setExpandedState(vscode.TreeItemCollapsibleState.Expanded);
    } else if (choice === choices[1]) {
        selectedNode.setExpandedState(vscode.TreeItemCollapsibleState.Collapsed);
    } else if (choice === choices[2]) {
        selectedNode.setSelected(true);
    } else if (choice === choices[3]) {
        selectedNode.setSelected(true, false);
    } else if (choice === choices[4]) {
        selectedNode.setSelected(false);
    } else if (choice === choices[5]) {
        selectedNode.setSelected(false, true);
    } else if (choice === 'Get Parent') {
        nextNode = parent;
    } else {
        let childNode = children.find(child => child.label === choice);
        nextNode = childNode;
    }
    if (nextNode) {
        let updatedNode = await azdata.objectexplorer.getNode(nextNode.connectionId, nextNode.nodePath);
        this.interactWithOENode(updatedNode);
    }
}

vscode.commands.registerCommand('mssql.objectexplorer.interact', () => {
    azdata.objectexplorer.getActiveConnectionNodes().then(activeConnections => {
        vscode.window.showQuickPick(activeConnections.map(connection => connection.label + ' ' + connection.connectionId)).then(selection => {
            let selectedNode = activeConnections.find(connection => connection.label + ' ' + connection.connectionId === selection);
            this.interactWithOENode(selectedNode);
        });
    });
});
```

## <a name="proposed-apis"></a>Предлагаемые интерфейсы API

Мы добавили предлагаемые интерфейсы API, которые, помимо прочего, позволяют расширениям отображать настраиваемый пользовательский интерфейс в диалоговых окнах, мастерах и на вкладках документов. Дополнительные сведения см. в [файле с типами предлагаемых интерфейсов API](https://github.com/Microsoft/azuredatastudio/blob/main/src/sql/azdata.proposed.d.ts), однако имейте в виду, что эти API могут быть изменены в любое время. Примеры использования некоторых из этих API можно найти в [примере расширения sqlservices](https://github.com/Microsoft/azuredatastudio/tree/main/samples/sqlservices).



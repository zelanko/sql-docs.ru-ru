---
title: API расширяемости
titleSuffix: Azure Data Studio
description: Дополнительные сведения о расширяемости API-интерфейсы для Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 55ab9fb45b37595c84303a5a52b83de14a05068d
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105253"
---
# <a name="azure-data-studio-extensibility-apis"></a>Azure Data Studio расширяемости API-интерфейсов

[!INCLUDE[name-sos](../includes/name-sos.md)] предоставляет интерфейс API, расширения можно использовать для взаимодействия с другими частями Studio данных Azure, такие как обозреватель объектов. Эти API доступны из [ `src/sql/sqlops.d.ts` ](https://github.com/Microsoft/azuredatastudio/blob/master/src/sql/sqlops.d.ts) файлов, которые описаны ниже.

## <a name="connection-management"></a>Управление подключениями
`sqlops.connection`

### <a name="top-level-functions"></a>Функции верхнего уровня

- `getCurrentConnection(): Thenable<sqlops.connection.Connection>` Получает текущее подключение, исходя из активного редактора или выбранного в обозревателе объектов.

- `getActiveConnections(): Thenable<sqlops.connection.Connection[]>` Получает список всех пользовательских подключений, которые активны. Возвращает пустой список, если подключения отсутствуют.

- `getCredentials(connectionId: string): Thenable<{ [name: string]: string }>` Возвращает словарь, содержащий учетные данные, связанные с подключением. Они в противном случае возвращаются в виде части в словарь параметров `sqlops.connection.Connection` объекта, но получить удаляются из этого объекта. 

### `Connection`
- `options: { [name: string]: string }` Словарь параметров соединения
- `providerName: string` Имя поставщика подключения (например) «MSSQL»)
- `connectionId: string` Уникальный идентификатор для подключения

### <a name="example-code"></a>Пример кода
```
> let connection = sqlops.connection.getCurrentConnection();
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
> let credentials = sqlops.connection.getCredentials(connection.connectionId);
credentials: {
    password: 'abc123'
}

```

## <a name="object-explorer"></a>обозревателе объектов

`sqlops.objectexplorer`


### <a name="top-level-functions"></a>Функции верхнего уровня
- `getNode(connectionId: string, nodePath?: string): Thenable<sqlops.objectexplorer.ObjectExplorerNode>` Получите соответствующий данного соединения и путь узла в обозревателе. Если путь не указан, он возвращает узел верхнего уровня для данного соединения. Если ни один узел по указанному пути, он возвращает `undefined`. Примечание. `nodePath` Для объекта создается служба средств SQL серверной частью и трудно создавать вручную. Улучшения в будущих обновлениях API, позволит вам получить узлы на основе метаданных, указанные вами сведения об узле, например имя, тип и схемы.

- `getActiveConnectionNodes(): Thenable<sqlops.objectexplorer.ObjectExplorerNode>` Получение всех активных узлах обозревателя объектов подключения.

- `findNodes(connectionId: string, type: string, schema: string, name: string, database: string, parentObjectNames: string[]): Thenable<sqlops.objectexplorer.ObjectExplorerNode[]>` Поиск всех узлов обозревателя объектов, соответствующих указанных метаданных. `schema`, `database`, И `parentObjectNames` аргументы должны быть `undefined` когда они не применяются. `parentObjectNames` Представляет список, не принадлежащего базе данных родительских объектов, от самого высокого до нижнего уровня в обозревателе объектов, в которой находится нужный объект в разделе. Например, при поиске столбец «column1», к которой принадлежит таблице «schema1.table1» и базы данных «database1» с Идентификатором соединения `connectionId`, вызовите `findNodes(connectionId, 'Column', undefined, 'column1', 'database1', ['schema1.table1'])`. Также см. в разделе [список типов, которые по умолчанию поддерживает Azure Data Studio](https://github.com/Microsoft/azuredatastudio/wiki/Object-Explorer-types-supported-by-FindNodes-API) для этого вызова API.

### <a name="objectexplorernode"></a>ObjectExplorerNode
- `connectionId: string` Идентификатор подключения, которое узел находится в

- `nodePath: string` Путь к узлу, как использовать для вызова `getNode` функции.

- `nodeType: string` Строка, представляющая тип узла

- `nodeSubType: string` Строка, представляющая подтип узла

- `nodeStatus: string` Строка, представляющая состояние узла

- `label: string` Метка для узла, так как он отображается в обозревателе объектов

- `isLeaf: boolean` Ли является конечным узлом узла и поэтому не имеет дочерних элементов

- `metadata: sqlops.ObjectMetadata` Метаданные, описывающие объект, представленный этим узлом

- `errorMessage: string` Сообщение отображается, если узел находится в состоянии ошибки

- `isExpanded(): Thenable<boolean>` Находится ли узел, раскрыв в обозревателе объектов

- `setExpandedState(expandedState: vscode.TreeItemCollapsibleState): Thenable<void>` Задается ли развернут или свернут узел. Если состояние имеет значение None, узел не изменится.

- `setSelected(selected: boolean, clearOtherSelections?: boolean): Thenable<void>` Задается ли узел выбран. Если `clearOtherSelections` имеет значение true, снимите все остальные флажки, при создании нового выделения. Если он имеет значение false, оставьте существующие параметры. `clearOtherSelections` по умолчанию имеет значение true, если `selected` имеет значение true и false, когда `selected` имеет значение false.

- `getChildren(): Thenable<sqlops.objectexplorer.ObjectExplorerNode[]>` Получите все дочерние узлы данного узла. Возвращает пустой список, если нет дочерних элементов.

- `getParent(): Thenable<sqlops.objectexplorer.ObjectExplorerNode>` Получает родительский узел данного узла. Возвращает не определено, если родительский элемент отсутствует.

### <a name="example-code"></a>Пример кода

```cs
private async interactWithOENode(selectedNode: sqlops.objectexplorer.ObjectExplorerNode): Promise<void> {
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
    let nextNode: sqlops.objectexplorer.ObjectExplorerNode = undefined;
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
        let updatedNode = await sqlops.objectexplorer.getNode(nextNode.connectionId, nextNode.nodePath);
        this.interactWithOENode(updatedNode);
    }
}

vscode.commands.registerCommand('mssql.objectexplorer.interact', () => {
    sqlops.objectexplorer.getActiveConnectionNodes().then(activeConnections => {
        vscode.window.showQuickPick(activeConnections.map(connection => connection.label + ' ' + connection.connectionId)).then(selection => {
            let selectedNode = activeConnections.find(connection => connection.label + ' ' + connection.connectionId === selection);
            this.interactWithOENode(selectedNode);
        });
    });
});
```

## <a name="proposed-apis"></a>Предложенный API-интерфейсов

Мы добавили предлагаемых API-интерфейсы для допускают использование расширений для отображения пользовательского интерфейса в диалоговые окна, мастера и вкладок документов, предоставляет другие возможности. См. в разделе [предложенное файл типы API](https://github.com/Microsoft/azuredatastudio/blob/master/src/sql/sqlops.proposed.d.ts) дополнительную документацию, однако учтите, что эти интерфейсы API не может быть изменена в любое время. Примеры того, как использовать некоторые из этих интерфейсов API можно найти в [«sqlservices» пример расширения](https://github.com/Microsoft/azuredatastudio/tree/master/samples/sqlservices).



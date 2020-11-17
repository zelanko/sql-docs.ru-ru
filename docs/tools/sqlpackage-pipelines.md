---
title: SqlPackage в конвейерах разработки
description: Сведения о том, как устранить проблемы с конвейерами разработки баз данных с помощью утилиты SqlPackage.exe путем проверки номера установленной сборки.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 198198e2-7cf4-4a21-bda4-51b36cb4284b
author: dzsquared
ms.author: drskwier
ms.reviewer: maghan; sstein
ms.date: 11/4/2020
ms.openlocfilehash: 14e54b44a5cfc40e98d1de9de1796630bb903b4f
ms.sourcegitcommit: 49ee3d388ddb52ed9cf78d42cff7797ad6d668f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2020
ms.locfileid: "94385227"
---
# <a name="sqlpackage-in-development-pipelines"></a>SqlPackage в конвейерах разработки

**SqlPackage.exe** — это программа командной строки, которая автоматизирует некоторые задачи разработки баз данных и которую можно внедрять в конвейеры CI/CD.

## <a name="managed-virtual-environments"></a>Управляемые виртуальные среды

Виртуальные среды, используемые для размещенных в GitHub Actions средствах выполнения тестов и образов виртуальных машин Azure Pipelines, управляются в репозитории [virtual-environments](https://github.com/actions/virtual-environments) на GitHub.  Утилита SqlPackage входит в состав среды `windows-latest`. Обновления образов становятся доступны в течение нескольких недель после каждого выпуска SqlPackage.

## <a name="checking-the-sqlpackage-version"></a>Проверка версии SqlPackage

При устранении неполадок очень важно знать, какая версия SqlPackage используется.  Получить эти данные можно, добавив в конвейер шаг для выполнения SqlPackage с параметром `/version`.  Ниже приведены примеры на основе управляемых сред Майкрософт и GitHub. В средах с самостоятельным размещением могут использоваться другие пути установки для рабочего каталога.

### <a name="azure-pipelines"></a>Azure Pipelines

Ключевое слово [script](https://docs.microsoft.com/azure/devops/pipelines/yaml-schema#script) в конвейере Azure Pipelines позволяет добавить шаг для вывода номера версии SqlPackage.

```yaml
- script: sqlpackage.exe /version
  workingDirectory: C:\Program Files\Microsoft SQL Server\150\DAC\bin\
  displayName: 'get sqlpackage version'
```

### <a name="github-actions"></a>Действия GitHub

Ключевое слово [run](https://docs.github.com/en/free-pro-team@latest/actions/reference/workflow-syntax-for-github-actions) в рабочем процессе GitHub Actions позволяет добавить шаг для вывода номера версии SqlPackage.

```yaml
- name: get sqlpackage version
  working-directory: C:\Program Files\Microsoft SQL Server\150\DAC\bin\
  run: ./sqlpackage.exe /version
```

:::image type="content" source="media/sqlpackage-pipelines-github-action.png" alt-text="Выходные данные действия GitHub с отображением номера версии 15.0.4897.1":::

## <a name="next-steps"></a>Дальнейшие шаги

- См. подробнее о [sqlpackage](sqlpackage.md)

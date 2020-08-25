---
title: Расширение центральных серверов управления SQL Server
description: Узнайте, как установить и использовать расширение "Центральные серверы управления" SQL Server (предварительная версия) для группирования серверов и применения действий к группе.
ms.reviewer: alayu, maghan, sstein
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.custom: seodec18
ms.date: 06/06/2019
ms.openlocfilehash: 3024a9c61fb51063b50f8fde769e7bdbb5608fbf
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88766053"
---
# <a name="sql-server-central-management-servers-extension-preview"></a>Расширение Центральных серверов управления SQL Server (предварительная версия)

Расширение центральных серверов управления позволяет пользователям хранить список экземпляров SQL Server, упорядоченный в одну или несколько групп. Действия, производимые с помощью группы центральных серверов управления, затрагивают все серверы в группе.

Сейчас это расширение находится на этапе начальной предварительной версии. Сообщить о проблемах и запросить функции можно [здесь](https://github.com/microsoft/azuredatastudio/issues).

![Расширение центральных серверов управления](media/sql-server-cms-extension/cms-list.png)

## <a name="install-the-sql-server-central-management-servers-extension"></a>Установка расширения центральных серверов управления SQL Server

1. Чтобы открыть диспетчер расширений и получить доступ к имеющимся расширениям, щелкните значок расширений или выберите пункт **Расширения** в меню **Вид**.
2. Выберите доступное расширение и просмотрите сведения о нем.
1. Выберите нужное расширение (центральные серверы управления SQL Server) и нажмите кнопку **Установить**.

### <a name="how-do-i-start-central-management-servers"></a>Как запустить центральные серверы управления?
 Чтобы просмотреть центральные серверы управления, можно щелкнуть значок "Подключения" (CTRL/CMD+G). При первом скачивании расширения представление центральных серверов управления будет свернуто и его можно открыть, щелкнув **Центральные серверы управления**.

## <a name="next-steps"></a>Дальнейшие действия
Дополнительные сведения о центральных серверах управления см. [ здесь](../ssms/register-servers/create-a-central-management-server-and-server-group.md).
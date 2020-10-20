---
title: Развертывание Базы данных SQL Azure через Notebook
description: В этом учебнике показано, как создать Базу данных SQL Azure.
author: ninarn
ms.author: ninarn
ms.reviewer: alayu, maghan
ms.topic: tutorial
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 10/14/2020
ms.openlocfilehash: 88bb9fd980da21b20f0faf6f699147d26abe65b9
ms.sourcegitcommit: 76ab3b57718341c6057613c9bd38cf82fb17786e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92060919"
---
# <a name="create-an-azure-sql-database-using-azure-data-studio"></a>Создание Базы данных SQL Azure с помощью Azure Data Studio

Вы можете создать базу данных SQL Azure с помощью Azure Data Studio, используя мастер развертывания и записные книжки.

## <a name="pre-requisites"></a>Предварительные требования

 - Установленное решение [Azure Data Studio](download-azure-data-studio.md).
 - Действующая учетная запись и подписка Azure. Если ее нет, создайте [бесплатную учетную запись](https://azure.microsoft.com/free/).

## <a name="use-the-deployment-wizard"></a>Использование мастера развертывания

Выполните следующие действия, чтобы использовать мастер развертывания, который поможет настроить необходимые параметры в простом интерфейсе пользователя.

Сначала найдите и выберите Базу данных SQL Azure в мастере развертывания.

 1. В Azure Data Studio выберите вьюлет "Подключения" на левой панели.
 2. Нажмите кнопку **...** в верхней части панели "Подключения" и выберите **Новое развертывание...**
 3. В мастере развертывания выберите плитку **База данных SQL Azure** и примите условия
 4. В раскрывающемся списке "Тип ресурса" выберите, что вы хотите создать — базу данных, сервер базы данных или пул эластичных баз данных. Если у вас нет баз данных SQL в Azure, мы рекомендуем начать с создания базы данных.
 5. Выберите **Создание на портале Azure**

Затем введите все предпочтительные параметры для создания базы данных, сервера или пула. Рекомендации по настройке этих параметров см. в [документации по SQL Azure](https://docs.microsoft.com/azure/azure-sql/database/single-database-create-quickstart?tabs=azure-portal).

## <a name="next-steps"></a>Дальнейшие действия

После создания базы данных, сервера или пула можно [подключиться и выполнить запрос](quickstart-sql-database.md) к базе данных в Azure Data Studio.

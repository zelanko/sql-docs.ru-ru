---
title: Установка & настройки базы данных dW WideWorldImporters
description: Следуйте этим инструкциям для загрузки, установки и настройки выборочной базы данных WideWorldImportersDW с помощью студии управления серверами S'L.
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 08/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.custom: seo-lt-2019
ms.openlocfilehash: 2f640415ecdc2ae4a48220aeec2a2c78ed79807c
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488560"
---
# <a name="wideworldimportersdw-installation-and-configuration"></a>Установка и конфигурация WideWorldImportersDW
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
Инструкции по установке и настройке базы данных WideWorldImportersDW.

- [База данных Лазурный сервер 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (или выше) или [База данных Azure S'L.](https://azure.microsoft.com/services/sql-database/) Для использования полной версии образца используйте s'L Server Evaluation/Developer/Enterprise Edition.
- [Студия управления серверами S'L](../ssms/download-sql-server-management-studio-ssms.md). Для достижения наилучших результатов используйте выпуск в июне 2016 года или позже.

## <a name="download"></a>Скачать

Последний выпуск образца:

[широкий мир-импортеров-релиз](https://go.microsoft.com/fwlink/?LinkID=800630)

Загрузите образец резервной базы данных WideWorldImportersDW, которая соответствует вашему изданию базы данных S'L Server или базы данных Azure S'L.

Исходный код для воссоздания выборочной базы данных доступен из следующего местоположения. Обратите внимание, что популяция данных основана на ETL из базы данных OLTP (WideWorldImporters):

[широкий мир-импортеров-источник](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/sample-scripts)

## <a name="install"></a>Установка


### <a name="sql-server"></a>SQL Server

Для восстановления резервного копирования в экземпляре сервера S'L можно использовать студию управления.

1. Откройте студию управления серверами и подключитесь к целевому экземпляру S'L Server.
2. Нажмите на узла **базы данных** и выберите **базу данных восстановления.**
3. Выберите **устройство** и нажмите на кнопку **...**
4. В диалоге **Выберите резервные устройства,** нажмите **Добавить,** перейти к резервной системе базы данных в файловой системе сервера, и выберите резервную копию. Нажмите кнопку **ОК**.
5. При необходимости измените целевое местоположение для файлов данных и журналов в панели **файлов файлов.** Обратите внимание, что лучше всего размещать данные и журналировать файлы на разных дисках.
6. Нажмите кнопку **ОК**. Это инициирует восстановление базы данных. После завершения, вы будете иметь базу данных WideWorldImporters установлен на вашем экземпляре сервера S'L.

### <a name="azure-sql-database"></a>База данных SQL Azure

Для импорта bacpac в новую базу данных S'L можно использовать студию управления.

1. (необязательно) Если у вас еще нет сервера S'L в Azure, перейдите на [портал Azure](https://portal.azure.com/) и создайте новую базу данных S'L. В процессе создания базы данных вы создадите сервер. Обратите внимание на сервер.
   - Смотрите [этот учебник,](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) чтобы создать базу данных в считанные минуты
2. Откройте студию управления серверами и подключитесь к серверу в Azure.
3. Нажмите на узлы **баз данных** и выберите **приложение Import Data-Tier.**
4. В **настройках импорта** выберите **Импорт из локального диска** и выберите бакпак базы данных образца из файловой системы.
5. В **настройках базы данных** изменение имени базы данных на *WideWorldImportersDW* и выбрать целевую цель и эксплуатации и службы.
6. Нажмите **далее** и **закончите,** чтобы начать развертывание. Этот процесс может занять несколько минут. При указании цели службы ниже S2 это может занять больше времени.

## <a name="configuration"></a>Конфигурация

«Применяется к серверу S'L 2016 (и более поздним) Разработчику/Оценке/Корпоративному Изданию»

Выборочная база данных может использоваться PolyBase для запроса файлов в хранилище Hadoop или Azure blob. Тем не менее, эта функция не установлена по умолчанию с помощью сервера S'L - ее необходимо выбрать во время установки сервера S'L Server. Поэтому требуется пост-установка шага.

1. В студии управления серверами S'L подключитесь к базе данных WideWorldImportersDW и откройте новое окно запроса.
2. Выполнить следующую команду T-S'L, чтобы включить PolyBase в базу данных:

   EXECUTE (Применение). (Configuration_ApplyPolyBase)

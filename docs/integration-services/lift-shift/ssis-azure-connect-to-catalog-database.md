---
title: Подключение к базе данных каталога SSISDB в Azure | Документы Майкрософт
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c9316c291ac650628bff880303c49822eca99700
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="connect-to-the-ssisdb-catalog-database-on-azure"></a>Подключение к базе данных каталога SSISDB в Azure

Получите сведения, необходимые для подключения к базе данных каталога SSISDB, размещенной на сервере базы данных SQL Azure. Для подключения вам потребуется следующее:
- Полное имя сервера
- Имя базы данных
- Данные для входа 

> [!IMPORTANT]
> В настоящее время невозможно создать базу данных каталога SSISDB в базе данных SQL Azure независимо от создания среды выполнения интеграции (IR) Azure-SSIS в фабрике данных Azure версии 2. Среда Azure-SSIS IR необходима для выполнения пакетов SSIS в Azure. Дополнительные сведения см. в разделе [Развертывание пакетов SSIS в Azure](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal). 

## <a name="prerequisites"></a>предварительные требования
Прежде чем начать, убедитесь в наличии SQL Server Management Studio (SSMS) версии 17.2 или более поздней. Если база данных каталога SSISDB размещается в управляемом экземпляре базы данных SQL (предварительная версия), убедитесь в наличии SSMS версии 17.6 или более поздней. Чтобы скачать последнюю версию SSMS, перейдите на страницу [скачивания SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="get-the-connection-info-from-the-azure-portal"></a>Получение сведений о подключении с портала Azure
1. Войдите на [портал Azure](https://portal.azure.com/).
2. На портале Azure выберите **Базы данных SQL** в левом меню и щелкните базу данных `SSISDB` на странице **Базы данных SQL**. 
3. На странице **Обзор** для базы данных `SSISDB` просмотрите полное имя сервера, как показано на следующем изображении. Наведите указатель мыши на имя сервера, чтобы отобразить параметр **Щелкните, чтобы скопировать**.

    ![Сведения о соединении с сервером](media/ssis-azure-connect-to-catalog-database/server-name.png) 

4. Если вы забыли учетные данные входа на сервер базы данных SQL, перейдите на страницу этого сервера. Там можно узнать имя администратора сервера и при необходимости сбросить пароль.

## <a name="connect-with-ssms"></a>Подключение к SSMS
1. Откройте среду SQL Server Management Studio.

2. **Подключение к серверу**. В диалоговом окне **Соединение с сервером** введите следующие данные:

   | Настройка       | Предлагаемое значение | Description | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Тип сервера** | Компонент Database Engine | Это значение обязательно. |
   | **Имя сервера** | Полное имя сервера | Имя должно быть в следующем формате: **mysqldbserver.database.windows.net**. |
   | **Проверка подлинности** | Проверка подлинности SQL Server | В этом кратком руководстве используется проверка подлинности SQL. |
   | **Имя входа** | Учетная запись администратора сервера | Это учетная запись, которая была указана при создании сервера. |
   | **Пароль** | Пароль для учетной записи администратора сервера | Это пароль, который был указан при создании сервера. |

    ![Подключение к серверу с помощью SSMS](media/ssis-azure-connect-to-catalog-database/ssisdb-connect-1.png)

3. **Подключитесь к базе данных SSISDB**. Чтобы развернуть диалоговое окно **Соединение с сервером**, выберите **Параметры**. В развернутом окне **Соединение с сервером** откройте вкладку **Свойства подключения**. В поле **Подключение к базе данных** выберите или введите `SSISDB`.

    > [!IMPORTANT]
    > Если вы не выбрали `SSISDB` при подключении, каталог служб SSIS в обозревателе объектов может не отображаться.

    ![Выбор базы данных SSISDB для подключения](media/ssis-azure-connect-to-catalog-database/ssisdb-connect-2.png)

4. В этом случае выберите **Подключиться**.

5. В обозревателе объектов разверните узел **Каталоги служб Integration Services** и затем узел **SSISDB** для просмотра объектов в базе данных каталога служб SSIS.

    ![Поиск базы данных SSISDB в обозревателе объектов в SSMS](media/ssis-azure-connect-to-catalog-database/ssisdb-connect-3.png)

## <a name="next-steps"></a>Следующие шаги
- Разверните пакет. Дополнительные сведения см. в разделе [Развертывание проекта служб SSIS с помощью SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Запустите пакет. Дополнительные сведения см. в разделе [Выполнение пакета служб SSIS с помощью SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).
- Создайте расписание для пакета. Дополнительные сведения см. в разделе [Планирование выполнения пакета служб SSIS в Azure](ssis-azure-schedule-packages.md).

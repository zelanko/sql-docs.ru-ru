---
title: "Подключения к базе данных каталога SSISDB в Azure | Документы Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 560965a241b24a09f50a23faf63ce74d0049d5a7
ms.openlocfilehash: ac121e600c3c616006d79892c50f796ca7cd6b3f
ms.contentlocale: ru-ru
ms.lasthandoff: 10/13/2017

---
# <a name="connect-to-the-ssisdb-catalog-database-on-azure"></a>Подключения к базе данных каталога SSISDB в Azure

Получите сведения о соединении, необходимые для подключения к базе данных каталога SSISDB, размещенная на сервере базы данных SQL Azure. Необходимые параметры для подключения.
- Полное имя сервера
- Имя базы данных
- сведения об имени входа 

## <a name="prerequisites"></a>Предварительные требования
Прежде чем начать, убедитесь, что у вас есть 17,2 или более поздней версии среды SQL Server Management Studio. Загрузить последнюю версию SSMS [загрузить SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="get-the-connection-info-from-the-azure-portal"></a>Получение сведений о подключении на портале Azure
1. Войдите на [портал Azure](https://portal.azure.com/).
2. На портале Azure выберите **баз данных SQL** из меню слева, а затем выберите `SSISDB` базы данных на **баз данных SQL** страницы. 
3. На **Обзор** страницы для `SSISDB` базы данных, просмотрите полное имя сервера, как показано на следующем рисунке. Наведите указатель мыши на имя сервера, чтобы подключить **нажмите, чтобы скопировать** параметр.

    ![Сведения о подключении сервера](media/ssis-azure-connect-to-catalog-database/server-name.png) 

4. Если вы забыли данные входа для базы данных SQL server, перейдите на страницу базы данных SQL server. Можно просмотреть администратор сервера имя и, при необходимости сбросить пароль.

## <a name="connect-with-ssms"></a>Подключитесь к SSMS
1. Откройте среду SQL Server Management Studio.

2. **Подключиться к серверу**. В **соединение с сервером** диалоговом окне введите следующие сведения:

   | Настройка       | Предлагаемое значение | Description | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Тип сервера** | Компонент Database Engine | Это значение обязательно. |
   | **Имя сервера** | Полное имя сервера | Имя должно быть в следующем формате: **mysqldbserver.database.windows.net**. |
   | **Проверка подлинности** | Проверка подлинности SQL Server | Это краткое руководство использует проверку подлинности SQL. |
   | **Имя входа** | Учетная запись администратора сервера | Это учетная запись, указанную при создании сервера. |
   | **Пароль** | Пароль для учетной записи администратора сервера | Это пароль, указанный при создании сервера. |

3. **Подключения к базе данных SSISDB**. Выберите **параметры** разверните **соединение с сервером** диалоговое окно. В развернутом **соединение с сервером** выберите **свойства соединения** вкладки. В **подключение к базе данных** выберите или введите `SSISDB`.

    > [!IMPORTANT]
    > Если вы не выбрали `SSISDB` при подключении, могут не отображаться в обозревателе объектов каталога служб SSIS.

4. Выберите **Connect**.

5. В обозревателе объектов разверните **каталоги служб Integration Services** и разверните **SSISDB** для просмотра объектов в базе данных каталога служб SSIS.

## <a name="next-steps"></a>Следующие шаги
- Развертывание пакета. Дополнительные сведения см. в разделе [развернуть проект служб SSIS с SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Запуск пакета. Дополнительные сведения см. в разделе [запуска пакета служб SSIS с SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).
- Запланируйте запуск пакета. Дополнительные сведения см. в разделе [пакета служб SSIS расписание выполнения в Azure](ssis-azure-schedule-packages.md)


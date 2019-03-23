---
title: Использование приложений в кластерах больших данных
titleSuffix: SQL Server 2019 big data clusters
description: Использование приложения, развернутого в кластере SQL Server 2019 больших данных, с помощью веб-службу RESTful (Предварительная версия).
author: jeroenterheerdt
ms.author: jterh
manager: craigg
ms.date: 03/18/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.reviewer: rothja
ms.openlocfilehash: a9ef02cae7899a1deb5ce6d84b10dac2297b9d2f
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58389962"
---
# <a name="consume-an-app-deployed-on-sql-server-big-data-cluster-using-a-restful-web-service"></a>Использовать приложение, развернутое в кластере SQL Server больших данных, с помощью веб-службу RESTful

В этой статье описывается, как использовать приложение, развернутое в кластере SQL Server 2019 больших данных, с помощью веб-службу RESTful (Предварительная версия).

## <a name="prerequisites"></a>предварительные требования

- [Кластер SQL Server 2019 больших данных](deployment-guidance.md)
- [Программа командной строки mssqlctl](deploy-install-mssqlctl.md)
- Приложения, развернутые с помощью либо [ `mssqlctl` ](big-data-cluster-create-apps.md) или [расширения развертывания приложения](app-deployment-extension.md)

## <a name="capabilities"></a>Возможности

После развертывания приложения в кластер SQL Server 2019 больших данных (Предварительная версия), вы можете получить доступ к и использовать приложение с помощью веб-службу RESTful. Это позволяет интеграции этого приложения из других приложений или служб (например, мобильное приложение или веб-сайта). В следующей таблице описаны команды развертывания приложения, которые можно использовать с **mssqlctl** для получения сведений о веб-службу RESTful для вашего приложения.

|Command |Описание |
|:---|:---|
|`mssqlctl app describe` | Описание приложения. |

Вы можете получить справку с `--help` параметра, как показано в следующем примере:

```bash
mssqlctl app describe --help
```

Следующие разделы описывают, как получить конечную точку для приложения и способы работы с веб-службу RESTful для интеграции приложений.

## <a name="retrieve-the-endpoint"></a>Получить конечную точку

**Mssqlctl приложения описывают** команда предоставляет подробные сведения о приложении, включая конечную точку в кластере. Обычно это используется, разработчик приложения для создания приложения с помощью клиента swagger и использование веб-службы для взаимодействия с приложением в RESTful-образом.

Описывающие ваше приложение, выполнив команду, аналогичную следующей:

```bash
mssqlctl app describe --name addpy --version v1
```

```json
{
  "input_param_defs": [
    {
      "name": "x",
      "type": "int"
    },
    {
      "name": "y",
      "type": "int"
    }
  ],
  "links": {
    "app": "https://10.1.1.3:30777/api/app/addpy/v1",
    "swagger": "https://10.1.1.3:30777/api/app/addpy/v1/swagger.json"
  },
  "name": "add-app",
  "output_param_defs": [
    {
      "name": "result",
      "type": "int"
    }
  ],
  "state": "Ready",
  "version": "v1"
}
```

Запишите IP-адрес (`10.1.1.3` в этом примере) и номер порта (`30777`) в выходных данных.

## <a name="generate-a-jwt-access-token"></a>Создать маркер доступа JWT

Чтобы получить доступ к веб-службу RESTful для приложения, которые вы развернули сначала необходимо создать маркер доступа JWT. Откройте в браузере следующий URL-адрес: `https://[IP]:[PORT]/api/docs/swagger.json` IP-адрес и порт, вы получили работает `describe` команды выше. Необходимо войти, используя те же учетные данные, используемые для `mssqlctl login`.

Вставить содержимое буфера `swagger.json` в [редактор Swagger](https://editor.swagger.io) чтобы понять, какие методы доступны:

![API-Интерфейс Swagger](media/big-data-cluster-consume-apps/api_swagger.png)

Обратите внимание, что `app` метод GET, а также `token` метод POST. Так как проверка подлинности для приложений используются маркеры JWT необходимо получить токен моей пользуясь своим любимым инструментом для выполнения вызова POST для `token` метод. Вот пример того, как именно для этого [Postman](https://www.getpostman.com/):

![Токен postman](media/big-data-cluster-consume-apps/postman_token.png)

Результат этого запроса обеспечит JWT `access_token`, который требуется вызывать URL-адрес для запуска приложения.

## <a name="execute-the-app-using-the-restful-web-service"></a>Выполнение приложения с помощью веб-службу RESTful

> [!NOTE]
> Если требуется, можно открыть URL-адрес для `swagger` , который был возвращен при запуске `mssqlctl app describe --name [appname] --version [version]` в браузере, который должен быть аналогичен `https://[IP]:[PORT]/api/app/[appname]/[version]/swagger.json`. Необходимо войти, используя те же учетные данные, используемые для `mssqlctl login`. Содержание `swagger.json` можно вставить в [редактор Swagger](https://editor.swagger.io). Вы увидите, что веб-служба предоставляет `run` метод. Также Обратите внимание, базовый URL-адрес, отображаемый в верхней.

Можно использовать для вызова одного из средств `run` метод (`https://[IP]:30778/api/app/[appname]/[version]/run`) с передачей параметров в тексте запроса POST как json. В этом примере мы будем использовать [Postman](https://www.getpostman.com/). Перед вызовом, вам потребуется задать `Authorization` для `Bearer Token` и вставьте в маркере, полученным ранее. Это будет значение заголовка запроса. См. на следующем снимке экрана.

![Postman запустите заголовки](media/big-data-cluster-consume-apps/postman_run_1.png)

Далее в тексте запросов передачи параметров в приложение, вы вызываете и задать `content-type` для `application/json`:

![Postman запустите текст](media/big-data-cluster-consume-apps/postman_run_2.png)

При отправке запроса вы получите те же выходные данные, как при запуске приложения `mssqlctl app run`:

![Результат выполнения postman](media/big-data-cluster-consume-apps/postman_result.png)

Вы успешно теперь называется приложения через веб-службы. Необходимо выполнить аналогичные действия для интеграции этой веб-службы в приложении.

## <a name="next-steps"></a>Следующие шаги

Вы можете также проверить Дополнительные примеры по [примеры развертывания приложений](https://aka.ms/sql-app-deploy).

Дополнительные сведения о больших данных кластеров SQL Server, см. в разделе [Каковы кластеров SQL Server 2019 больших данных?](big-data-cluster-overview.md).

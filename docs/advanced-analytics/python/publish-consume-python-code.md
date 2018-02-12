---
title: "Публикация и использование кода Python | Документы Microsoft"
ms.custom: 
ms.date: 11/09/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 8720440872fb0b41a76d4ac644fd3b60d52a095e
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2018
---
# <a name="publish-and-consume-python-web-services"></a>Публикация и использование Python веб-служб
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Можно развернуть рабочее решение Python в веб-службу с помощью функции ввода в эксплуатацию в Microsoft Server обучения машины. В этом разделе описывается для успешной публикации и запуска решения.

В этой статье предназначен для специалистов по анализу данных, чтобы узнать, как опубликовать как веб-службы, размещается в Microsoft Server обучения машины кода Python или модели. Здесь также описывается, как приложения могут использовать в коде или модель. В этой статье предполагается, что вы специализация Python.

> [!IMPORTANT]
>
> Этот образец разработан для версии Python, входит в состав машины обучения Server (изолированный) и использует возможности в версии сервера обучения машины **9.1.0**.
 > 
 > Выберите следующую ссылку, см. в примере же опубликовать повторно с помощью библиотеки более новой версии в Machine Learning Server. В разделе [развертывание и управление веб-службами в Python](https://docs.microsoft.com/machine-learning-server/operationalize/python/how-to-deploy-manage-web-services).

**Применяется к: Microsoft R Server (изолированный)**

## <a name="overview-of-workflow"></a>Обзор рабочего процесса

Рабочий процесс публикации для этого веб-служба Python можно интерпретировать следующим образом:

1. Выполнить [необходимого компонента](#prereq) создания клиентской библиотеки Python из документа API Swagger core.
2. Добавьте логику проверки подлинности и заголовок сценарий Python.
3. Создание сеанса Python, подготовьте среду и создание моментального снимка для сохранения среды.
4. Опубликовать веб-службу и внедрить этот моментальный снимок.
5. Пробное использование веб-службы путем использования ее в текущем сеансе.
6. Управление этими службами.

![Swagger рабочего процесса](./media/data-scientist-python-workflow.png)

В этой статье рассматривается каждый шаг рабочего процесса и приведен пример кода Python, с помощью набора данных iris.

## <a name="sample-code"></a>Образец кода

Этот пример кода предполагает вы выполнили требования [необходимые компоненты](#prereq) для создания клиентской библиотеки Python из Swagger этот файл и что использовали Autorest.

После блока кода вы найдете Пошаговое руководство с более подробное описание всего процесса.

> [!IMPORTANT]
> В этом примере используется локальная `admin` учетной записи для проверки подлинности. Тем не менее, следует заменить учетные данные и [метод проверки подлинности](#python-auth) настроенный администратором.

```python
##################################################
##       IMPORT GENERATED CLIENT LIBRARY        ##
##################################################

# Import the generated client library. 

import deployrclient

# This example is intended for use with Microsoft R Server 9.0.1. 
# If you are using a newer version of Machine Learning Server, 
# use the mrs_server library instead.

##################################################
##              AUTHENTICATION                  ##
##################################################

#Using client library generated from Autorest
#Create client instance and point it at an R Server. 
#In this case, R Server is local.
client = deployrclient.DeployRClient("http://localhost:12800")
# To use ML Server, replace with mrs_server.MRSServer()

#Define the login request and provide credentials 
#Update values with the connection parameters from your admin
login_request = deployrclient.models.LoginRequest("<<your-username>>","<<your-password>>")

#Make a call to the /login API. 
#Store the returned an access token in a variable.
token_response = client.login(login_request)

#Add the returned access token to the headers variable.
headers = {"Authorization": "Bearer {0}".format(token_response.access_token)}

#Verify that the server is running.
#Remember to include `headers` in all requests!
status_response = client.status(headers) 
print(status_response.status_code)


##################################################
##        CREATE SESSION, MODEL, SNAPSHOT       ##
##################################################

#Since already logged in, create a Python session.
#Define session using name (`Session 1`) and `runtime_type="Python"`.
#Remember to specify the Python runtime type.
create_session_request = deployrclient.models.CreateSessionRequest("Session 1", runtime_type="Python")

#Make the call to start the session. 
#Remember to include headers in all method calls to the server.
#Returns a session ID.
response = client.create_session(create_session_request, headers) 
   
#Store the session ID in a variable called `session_id` 
#to be able to identify it later at execution time.
session_id = response.session_id

#Create model - Import SVM and datasets from the SciKit-Learn library
execute_request = deployrclient.models.ExecuteRequest("from sklearn import svm\nfrom sklearn import datasets")
execute_response = client.execute_code(session_id,execute_request, headers)
#Report if it was a success
execute_response.success
   
#Define the untrained Support Vector Classifier (SVC) object
#and the dataset to be preloaded.
execute_request = deployrclient.models.ExecuteRequest("clf=svm.SVC()\niris=datasets.load_iris()\nnames={0:'I. setosa',1:'I. versicolor',2:'I. virginica'}")
#Now, go create the object and preload Iris Dataset in R Server
execute_response = client.execute_code(session_id,execute_request, headers)
#Report if it was a success
execute_response.success
   
#Define two rows from the Iris Dataset as a sample for scoring
workspace_object = deployrclient.models.WorkspaceObject("species_1",[7,3.2,4.7,1.4])
workspace_object_2 = deployrclient.models.WorkspaceObject("species_2",[3,2.6,3,2.5])

#Define how to train the classifier model; what to predict; what to return
execute_request = deployrclient.models.ExecuteRequest(
    "clf.fit(iris.data, iris.target)\n"+
    "result=clf.predict(species_1)\n"+
    "other_result=clf.predict(species_2)",
    [workspace_object,workspace_object_2], #Input
    ["result", "other_result"]) #Output

#Now, go train that model on the Iris Dataset in R Server
execute_response = client.execute_code(session_id,execute_request, headers)

#If successful, print name and result of each output parameter. Else, print error.
if(execute_response.success):
    for result in execute_response.output_parameters:
        print("{0}: {1}".format(result.name,result.value))
else:
    print (execute_response.error_message)

#Create a snapshot of the current session
response = client.create_snapshot(session_id, deployrclient.models.CreateSnapshotRequest("Iris Snapshot"), headers)
#Return the snapshot ID for reference when you publish later.
response.snapshot_id
#If you forget the ID, list snapshots to get the ID again.
for snapshot in client.list_snapshots(headers):
    print(snapshot)

##################################################
##        PUBLISH AS A SERVICE IN PYTHON        ##
##################################################

#Define a web service that determines the iris species by scoring 
#a vector of sepal length and width, petal length and width

#Set `flower_data` for the sepal and petal length and width
flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
#Set `iris_species` for the species of iris
iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "vector")

#Define the publish request for the web service and its arguments.
#Specify the code, inputs, outputs, and snapshot.
#Don't forget to set runtime_type="Python"`.
publish_request = deployrclient.models.PublishWebServiceRequest(
       code = "iris_species = [names[x] for x in clf.predict(flower_data)]", 
       input_parameter_definitions = [flower_data], 
       output_parameter_definitions = [iris_species],
       runtime_type = "Python",
       snapshot_id = response.snapshot_id)

#Publish the service using the specified name (iris), version (V1.0)
client.publish_web_service_version("Iris", "V1.0", publish_request, headers)

##################################################
##           CONSUME SERVICE IN PYTHON          ##
##################################################

# Inspect holdings and metadata for service Iris V1.0.
for service in client.get_web_service_version("Iris","V1.0", headers):
    #print service metadata (description, who published,...)
    print(service)
    #Print input and output parameters as defined in service definition object
    print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
    print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))

#Import the requests library to make requests on the server
import requests
#Import the JSON library to use for pretty printing of json responses
import json

#Create a requests `Session` object.
s = requests.Session()

#Record the R Server endpoint URL hosting the web services you created before
url = "http://localhost:12800"

#Give the request.Session object the authentication headers 
#so you don't have to repeat it with each request.
s.headers = headers

#Retrieve the service-specific swagger file using the requests library.
swagger_resp = s.get(url+"/api/Iris/V1.0/swagger.json")

#Either, download service-specific swagger file using the json library.
with open('iris_swagger.json','w') as f:
   (json.dump(client.get_web_service_swagger("Iris","V1.0",headers),f, indent = 1))

#Or, print just what you need from the Swagger file, 
#such as the routing paths for the endpoints to be consumed.
print(json.dumps(swagger_resp.json()["paths"], indent = 1, sort_keys = True))

#Or, print input and output parameters as defined in the Swagger.io format
print("Input")
print(json.dumps(swagger_resp.json()["definitions"]["InputParameters"], indent = 1, sort_keys = True))
print("Output")
print(json.dumps(swagger_resp.json()["definitions"]["WebServiceResult"], indent = 1, sort_keys = True))

#Make the request to consume the service using these flower_data inputs
resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[7,3.2,4.7,1.4]})
#Print the output
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

#Use input from another Iris species.
resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[3,2.6,3,2.5]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

#Use input from another Iris species.
resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[5.1,3.5,1.4,.2]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

##################################################
##          MANAGE SERVICES IN PYTHON           ##
##################################################

#Define what needs to be updated. Here we add a description.
#Be sure to specify the runtime_type again.
update_request = deployrclient.models.PublishWebServiceRequest(
    description = "Determines iris species using length and width of sepal and petal", runtime_type = "Python")
#Now update it by specifying the service name and version number
client.patch_web_service_version("Iris", "V1.0", update_request, headers)

#Or, publish another version of the web service, but this time 
#the service returns the species as a string instead of list of strings.
flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "string")
 
#Define the publish request for the service and its arguments.
#Specify the changed code, inputs, outputs, and snapshot.
#Don't forget to set runtime_type="Python"`.
publish_request = deployrclient.models.PublishWebServiceRequest(
    code = "iris_species = [names[x] for x in clf.predict(flower_data)][0]",
    description = "Determines the species of iris, based on Sepal Length, Sepal Width, Petal Length and Petal Width",
    input_parameter_definitions = [flower_data],
    output_parameter_definitions = [iris_species],
    runtime_type = "Python",
    snapshot_id = response.snapshot_id)
 
#Now, publish the service with version (V2.0)
client.publish_web_service_version("Iris", "V2.0", publish_request, headers)
 
#Make request to consume service using these flower_data inputs; print output
resp = s.post(url+"/api/Iris/V2.0",json={"flower_data":[5.1,3.5,1.4,.2]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

#Return the list of all existing web services.
for service in client.get_all_web_services(headers):
    #print the service information
    print(service)
    #Print each input and output parameter
    print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
    print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))

#Delete the second version we just published.
client.delete_web_service_version("Iris","V2.0",headers)
```

## <a name="walkthrough"></a>Пошаговое руководство

В этом разделе описывается, как работает код более подробно.


### <a name="prereq"></a>Шаг 1. Создание необходимых клиентских библиотек

Перед началом публикации вашей Python кода и модели с помощью порядкового Microsoft Server обучения машины, необходимо создать библиотеку клиента, с помощью Swagger документа, выделенный для этого выпуска.

1. Установите генератор кода Swagger на локальном компьютере и ознакомиться с ним. Используется для создания клиентских библиотек API в Python. Популярные средства включают в себя [Azure AutoRest](https://github.com/Azure/autorest) (требуется Node.js) и [Swagger Codegen](https://github.com/swagger-api/swagger-codegen). 

2. Загрузите файл Swagger, содержащий базовые интерфейсы API для используемой версии сервера Machine обучения. Этот файл содержит Swagger шаблон, определив список REST ресурсов и операций, которые могут вызываться с этими ресурсами. Можно найти этот файл под `https://microsoft.github.io/deployr-api-docs/swagger/<version>/rserver-swagger-<version>.json`, где `<version>` является номером версии R Server 3 цифры. 

   Например, для R Server 9.1 будет загружено с: https://microsoft.github.io/deployr-api-docs/9.1.0/swagger/rserver-swagger-9.1.0.json

3. Создание статически созданные клиентской библиотеке, передав `rserver-swagger-<version>.json` файла в генератор кода Swagger и, задающее язык. В этом случае следует указать Python.  

    Например если AutoRest использовать для создания клиентской библиотеки Python, он может выглядеть следующим образом, где 3-значное число представляет номер версии R Server:
    
    `AutoRest.exe -Input rserver-swagger-9.1.0.json -CodeGenerator Python  -OutputDirectory C:\Users\rserver-user\Documents\Python`

4. Можно также предоставляют некоторые настраиваемые заголовки и вносить другие изменения перед началом использования созданного клиента библиотеки заглушки. В разделе [Command Line Interface](https://github.com/Azure/autorest/blob/master/docs/user/cli.md) сведения о различные параметры конфигурации и настройки, таких как переименование пространство имен документации на сайте GitHub.
   
5. Просмотрите основной библиотеки клиента для просмотра различных API-вызовами, которые можно выбрать. 

    В нашем примере Autorest создан некоторые каталоги и файлы для клиентской библиотеки Python в локальной системе. По умолчанию пространство имен (и каталог) является `deployrclient` и может выглядеть следующим образом:
   
   ![Выходной путь Autorest](./media/data-scientist-python-autorest.png)

    Для этого пространства имен по умолчанию, называется клиентской библиотеке сам `deploy_rclient.py`. При открытии этого файла в вашей разработки, такой как Visual Studio, вы увидите примерно следующим образом:
   
   ![Библиотека клиентов Python](./media/data-scientist-python-client-library.png)


### <a name="step-2-add-authentication-and-header-logic"></a>Шаг 2. Добавьте логику проверки подлинности и заголовок

Следует помнить, что все интерфейсы API требуется проверка подлинности; Таким образом, все пользователи должен пройти проверку подлинности при выполнении вызовы с использованием API `POST /login` API или через Azure Active Directory (AAD). 

Чтобы пользователям не обязательно предоставлять свои учетные данные для каждого вызова, чтобы упростить этот процесс, выдаются маркеры доступа носителя.  Этот токен носителя является это упрощенный токен безопасности, предоставляющий «предъявителю» доступ к защищенному ресурсу: в этом случае на компьютере сервер обучения API-интерфейсы. После проверки подлинности пользователя приложение должно проверить пользовательский маркер носителя, чтобы убедиться в успешности проверки подлинности для предполагаемых сторон. Дополнительные сведения об управлении этих токенов см. в разделе [маркера безопасного доступа](https://msdn.microsoft.com/microsoft-r/operationalize/security-access-tokens).

Перед общением с базовые интерфейсы API, сначала выполнить проверку подлинности, получить доступ на предъявителя токена с помощью [метод проверки подлинности](https://msdn.microsoft.com/microsoft-r/operationalize/security-authentication) настроенный администратором, а затем включить ее в каждом верхнем колонтитуле для каждого последующего запроса:

1. Начните работу с импорта клиентской библиотеки, чтобы сделать его доступным в ваш основной Python редактор кода, например Jupyter, Visual Studio, VS Code или iPython.

   Укажите родительский каталог клиентской библиотеки. В нашем примере созданный клиентской библиотеке Autorest меньше `C:\Users\rserver-user\Documents\Python\deployrclient`:

   ```python
   # Import the generated client library
   import deployrclient
   ```

2. Добавьте логику проверки подлинности в приложение, чтобы определить соединение с локального компьютера с сервером обучения машины, учетные данные, записать маркер доступа, добавьте этот токен в заголовок. Заголовок, которые будут использоваться для всех последующих запросов.  Использование метода проверки подлинности, определенных администратором: учетная запись администратора, basic, Active Directory или LDAP (AD или LDAP) или Azure Active Directory (AAD).

   **AD или LDAP или `admin` проверка подлинности учетной записи**

   Вызовите `POST /login` API для проверки подлинности. Передайте `username` и `password` для локального администратора, или если Active Directory включена, сведения об учетной записи LDAP. В свою очередь компьютере обучения сервер выдает маркер носителя или доступа. После проверки подлинности пользователя больше нет необходимости предоставить учетные данные еще раз, при условии, что маркер еще действителен и заголовок передается с каждым запросом. Если вы не знаете параметры подключения, обратитесь к администратору.

   ```python
   #Using client library generated from Autorest
   #Create client instance and point it at an R Server. 
   #In this case, R Server is local.
   client = deployrclient.DeployRClient("http://localhost:12800")
   
   #Define the login request and provide credentials. 
   #Update values with the connection parameters from your admin.
   login_request = deployrclient.models.LoginRequest("<<your-username>>","<<your-password>>")
   #Make a call to the /login API. 
   #Store the returned an access token in a variable.
   token_response = client.login(login_request)
   ```

   **Проверка подлинности Azure Active Directory (AAD)**

   Передать учетные данные AAD, сертификацией и идентификатор клиента. В свою очередь, выдает AAD [токен доступа носителя](https://msdn.microsoft.com/microsoft-r/operationalize/security-access-tokens). После проверки подлинности пользователя больше нет необходимости предоставить учетные данные еще раз, при условии, что маркер еще действителен и заголовок передается с каждым запросом. Если вы не знаете параметры подключения, обратитесь к администратору.

   ```python
   #Import the AAD authentication library
   import adal
   
   #Define the login request and provide credentials. 
   #Use the AAD connection parameters provided by your admin.
   url = "http://localhost:12800"
   authuri = https://login.windows.net,
   tenantid = "<<AAD_DOMAIN>>", 
   clientid = "<<NATIVE_APP_CLIENT_ID>>", 
   resource = "<<WEB_APP_CLIENT_ID>>", 
   
   #Acquire authentication token using AAD Device Code Login
   context = adal.AuthenticationContext(authuri+'/'+tenantid, api_version=None)
   code = context.acquire_user_code(resource, clientid)
   print(code['message'])
   token = context.acquire_token_with_device_code(resource, code, clientid)
   #The authentication code returned must be entered at https://aka.ms/devicelogin 
   ```     

3. Добавить `Bearer` доступ к маркер и убедитесь, что машины обучения сервера выполняется в данный момент.  Этот маркер был возвращен во время проверки подлинности и **должен быть включен в заголовок каждого последующего запроса**. Этот пример использует клиентскую библиотеку, создаваемые Autorest.

   > [!IMPORTANT]
   > Все вызовы API должен пройти проверку подлинности. Таким образом не забудьте включить заголовки с маркерами для каждого запроса.

   ```python
   #Add the returned access token to the headers variable.
   headers = {"Authorization": "Bearer {0}".format(token_response.access_token)}
   
   #Verify that the server is running.
   #Remember to include `headers` in every request!
   status_response = client.status(headers) 
   print(status_response.status_code)
   ```

### <a name="step-3-prepare-session-and-code"></a>Шаг 3. Подготовка сеанса и кода

После проверки подлинности можно начать сеанс Python и создать модель для публикации в более поздней версии. Можно включать кода Python или моделей в веб-службы. После настройки среды сеанса можно даже сохранить его как моментальный снимок, можно перезагрузить сеанс, как был до. 

> [!IMPORTANT]
> Не забудьте включить `headers` в каждом запросе.

1. Создайте сеанс Python R Server. Необходимо указать имя и язык Python (`runtime_type="Python"`).  Если не задан тип среды выполнения Python, то по умолчанию R.

   Это продолжение данного примера с помощью клиентской библиотеки, создаваемые Autorest:

   ```python
   #Since already logged in, create a Python session.
   #Define session using name (`Session 1`) and `runtime_type="Python"`.
   #Remember to specify the Python runtime type.
   create_session_request = deployrclient.models.CreateSessionRequest("Session 1", runtime_type="Python")
   
   #Make the call to start the session. 
   #Remember to include headers in every method call to the server.
   #Returns a session ID.
   response = client.create_session(create_session_request, headers) 
   
   #Store the session ID in a variable called `session_id` 
   #to be able to identify it later at execution time.
   session_id = response.session_id
   ```

2. Создание и вызов модели в Python, который будет публиковать веб-службы

   В этом примере мы обучение узнать SciKit модель опорных векторов векторов (SVM) в набор данных Iris на удаленном экземпляре сервера Machine обучения.  Этот набор данных доступен из [scikit-узнать сайта](http://scikit-learn.org/stable/auto_examples/datasets/plot_iris_dataset.html).

   ```python
   #Import SVM and datasets from the SciKit-Learn library
   execute_request = deployrclient.models.ExecuteRequest("from sklearn import svm\nfrom sklearn import datasets")
   execute_response = client.execute_code(session_id,execute_request, headers)
   #Report if it was a success
   execute_response.success
   
   #Define the untrained Support Vector Classifier (SVC) object
   #and the dataset to be preloaded.
   execute_request = deployrclient.models.ExecuteRequest("clf=svm.SVC()\niris=datasets.load_iris()\nnames={0:'I. setosa',1:'I. versicolor',2:'I. virginica'}")
   #Now, go create the object and preload Iris Dataset in R Server
   execute_response = client.execute_code(session_id,execute_request, headers)
   #Report if it was a success
   execute_response.success
   
   #Define two rows from the Iris Dataset as a sample for scoring
   workspace_object = deployrclient.models.WorkspaceObject("species_1",[7,3.2,4.7,1.4])
   workspace_object_2 = deployrclient.models.WorkspaceObject("species_2",[3,2.6,3,2.5])

   #Define how to train the classifier model; what to predict; what to return
   execute_request = deployrclient.models.ExecuteRequest(
       "clf.fit(iris.data, iris.target)\n"+
       "result=clf.predict(species_1)\n"+
       "other_result=clf.predict(species_2)",
       [workspace_object,workspace_object_2], #Input
       ["result", "other_result"]) #Output

   #Now, go train that model on the Iris Dataset in R Server
   execute_response = client.execute_code(session_id,execute_request, headers)

   #If successful, print name and result of each output parameter. Else, print error.
   if(execute_response.success):
       for result in execute_response.output_parameters:
           print("{0}: {1}".format(result.name,result.value))
   else:
       print (execute_response.error_message)
   ```

3. Создать моментальный снимок из этого Python сеанса, поэтому в этой среде можно сохранить в веб-службе и воспроизвести на равно времени. Моментальные снимки полезны в тех случаях, когда требуется среды с подготовленной, которая включает определенных библиотек, объекты, моделей, файлы и артефакты. Моментальные снимки сохранить всей рабочей области и рабочий каталог. Тем не менее при публикации, можно использовать только моментальные снимки, которые вы создали.

   ```python
   #Create a snapshot of the current session.
   response = client.create_snapshot(session_id, deployrclient.models.CreateSnapshotRequest("Iris Snapshot"), headers)
   
   #Return the snapshot ID for reference when you publish later.
   response.snapshot_id
   
   #If you forget the ID, list snapshots to get the ID again.
   for snapshot in client.list_snapshots(headers):
       print(snapshot)
   ```

  > [!NOTE] 
   > Хотя также можно использовать моментальные снимки, при публикации веб-службы для зависимостей среды, он может оказывать влияние на производительность, потребление времени.  Для оптимальной производительности следует внимательно рассмотреть размер моментального снимка и убедитесь, что только рабочей объекты нужно и удалить остальные. В рамках сеанса, можно использовать Python `del` функции или [ `deleteWorkspaceObject` запроса API](https://microsoft.github.io/deployr-api-docs/#delete-workspace-object) для удаления ненужных объектов. 

### <a name="step-4-publish-the-model"></a>Шаг 4. Опубликовать модель 

После библиотеку клиента был создан и вы создали логики проверки подлинности в приложение, вы можете взаимодействовать с основной API для создания сеанса Python, создания модели и затем опубликовать веб-службу, с помощью этой модели.

Необходимо помнить следующее:

+ Необходимо пройти проверку подлинности перед внесением каких-либо вызовов API. Таким образом, включать `headers` во всех запросах.
+ Чтобы убедиться, что веб-службы зарегистрировано как служба Python, не забудьте указать `runtime_type="Python"`. Если не задан тип среды выполнения Python, то по умолчанию R.
+ Оценки требует вектор с sepal длины, ширина sepal, лепесток длины и ширины лепесток

Следующий код публикует модели SVM Python веб-службы. Эта веб-служба создает прогнозируемых на основе значений, переданных ему категорию.

```python
   #Set `flower_data` for the sepal and petal length and width
   flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
   #Set `iris_species` for the species of iris
   iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "vector")
   
   #Define the publish request for the web service and its arguments.
   #Specify the code, inputs, outputs, and snapshot.
   #Don't forget to set runtime_type="Python"`.
   publish_request = deployrclient.models.PublishWebServiceRequest(
       code = "iris_species = [names[x] for x in clf.predict(flower_data)]", 
       input_parameter_definitions = [flower_data], 
       output_parameter_definitions = [iris_species],
       runtime_type = "Python",
       snapshot_id = response.snapshot_id)

   #Publish the service using the specified name (iris), version (V1.0)
   client.publish_web_service_version("Iris", "V1.0", publish_request, headers)
```

### <a name="step-5-consume-the-web-service"></a>Шаг 5. Использовать веб-службы

В этом разделе показано, как пользоваться службой, в том же сеансе, в котором он был создан.

1. В том же сеансе получения средствами службы и метаданных для службы.

   ```python
   # Inspect holdings and metadata for service Iris V1.0.
   for service in client.get_web_service_version("Iris","V1.0", headers):
       #print service metadata (description, who published,...)
       print(service)
       #Print input and output parameters as defined in service definition object
       print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
       print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))
   ```

2. Проверьте активах службы и подготовка для использования. 
   ```python
   #Import the requests library to make requests on the server
   import requests
   #Import the JSON library to use for pretty printing of json responses
   import json

   #Create a requests `Session` object.
   s = requests.Session()

   #Record the R Server endpoint URL hosting the web services you created
   url = "http://localhost:12800"

   #Include the request.Session object in the authentication headers.
   #By doing so, you don't need to repeat it with each request.
   s.headers = headers

   # Retrieve the service-specific Swagger file using the requests library.
   swagger_resp = s.get(url+"/api/Iris/V1.0/swagger.json")

   #You can download a service-specific Swagger file using the json library.
   with open('iris_swagger.json','w') as f:
      (json.dump(client.get_web_service_swagger("Iris","V1.0",headers),f, indent = 1))

   #Or, you can print just what you need from the Swagger file. 
   #This example gets the routing paths for the endpoints to be consumed.
   print(json.dumps(swagger_resp.json()["paths"], indent = 1, sort_keys = True))

   #You can also print input and output parameters as defined in the Swagger.io format
   print("Input")
   print(json.dumps(swagger_resp.json()["definitions"]["InputParameters"], indent = 1, sort_keys = True))
   print("Output")
   print(json.dumps(swagger_resp.json()["definitions"]["WebServiceResult"], indent = 1, sort_keys = True))
   ```

3. Использовать службу, указав некоторых входных данных и получение указывает Iris. 
   ```python
   #Make the request to consume the service using these flower_data inputs
   resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[7,3.2,4.7,1.4]})
   #Print the output
   print(json.dumps(resp.json(), indent = 1, sort_keys = True))

   ##Use input from another Iris species.
   resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[3,2.6,3,2.5]})
   print(json.dumps(resp.json(), indent = 1, sort_keys = True))

   ##Use input from another Iris species.
   resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[5.1,3.5,1.4,.2]})
   print(json.dumps(resp.json(), indent = 1, sort_keys = True))
   ```

## <a name="managing-the-services"></a>Управление службами

После создания веб-службы можно обновить, удалить или повторно опубликовать эту службу. Можно составить список всех веб-служб, размещенных с помощью R Server (или сервера обучения Machine).

### <a name="update-a-web-service"></a>Обновление веб-службы

 В этом примере обновления службы, чтобы добавить описание полезных для людей, которые могут использовать эту службу.

```python
#Define what needs to be updated. Here we add a description.
#Be sure to specify the runtime_type again.
update_request = deployrclient.models.PublishWebServiceRequest(
    description = "Determines iris species using length and width of sepal and petal", runtime_type = "Python")
#Now update it by specifying the service name and version number
client.patch_web_service_version("Iris", "V1.0", update_request, headers)
```

Вы можете обновить веб-службы, чтобы изменить код, модели, описание, входов, выходов и многое другое.

### <a name="publish-another-version"></a>Другой версии публикации

В этом примере служба теперь возвращают указывает Iris как строки, а не как список строк.

```python
#Publish another version of the web service, but this time 
#the service returns the species as a string instead of list of strings.
flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "string")
 
#Define the publish request for the service and its arguments.
#Specify the changed code, inputs, outputs, and snapshot.
#Don't forget to set runtime_type="Python"`.
publish_request = deployrclient.models.PublishWebServiceRequest(
    code = "iris_species = [names[x] for x in clf.predict(flower_data)][0]",
    description = "Determines the species of iris, based on Sepal Length, Sepal Width, Petal Length and Petal Width",
    input_parameter_definitions = [flower_data],
    output_parameter_definitions = [iris_species],
    runtime_type = "Python",
    snapshot_id = response.snapshot_id)
 
#Now, publish the service with version (V2.0)
client.publish_web_service_version("Iris", "V2.0", publish_request, headers)
 
#Make request to consume service using these flower_data inputs; print output
resp = s.post(url+"/api/Iris/V2.0",json={"flower_data":[5.1,3.5,1.4,.2]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))
```

Этот шаблон можно использовать для публикации нескольких версий одной веб-службы. 

### <a name="list-services"></a>Перечисление служб

Этот пример возвращает список всех веб-служб, включая созданные другими пользователями или на разных языках.

```python
#Return the list of all existing web services.
for service in client.get_all_web_services(headers):
    #print the service information
    print(service)
    #Print each input and output parameter
    print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
    print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))
``` 

### <a name="delete-services"></a>Удаление служб

В этом примере мы удалить второй веб-версию службы мы публикации.

```python
#Delete the second version we just published.
client.delete_web_service_version("Iris","V2.0",headers)
```

Можно удалить все службы, которые вы создали. Службы других компаний можно удалить только в том случае, если вы назначены роли, которая имеет соответствующие разрешения.
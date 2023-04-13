<a href="https://github.com/wiseupdata/wiseupdata">
  <img align="left" alt="Wise Up Data's Instagram" width="22px" src="https://raw.githubusercontent.com/wiseupdata/wiseupdata/main/assets/instagram.png" />   
</a> 
<a href="https://github.com/wiseupdata/wiseupdata">
  <img align="left" alt="wise Up Data's Discord" width="22px" src="https://raw.githubusercontent.com/wiseupdata/wiseupdata/main/assets/discord.png" />
</a>
<a href="https://github.com/wiseupdata/wiseupdata">
  <img align="left" alt="wise Up Data | Twitter" width="22px" src="https://raw.githubusercontent.com/wiseupdata/wiseupdata/main/assets/twitter.png" />
</a>
<a href="https://github.com/wiseupdata/wiseupdata">
  <img align="left" alt="wise Up Data's LinkedIN" width="22px" src="https://raw.githubusercontent.com/wiseupdata/wiseupdata/main/assets/linkedin.png" />
</a>

![visitors](https://visitor-badge.glitch.me/badge?page_id=wiseupdata.databricks&left_color=green&right_color=black)
![license](https://img.shields.io/github/license/wiseupdata/databricks)

---

<a name="readme-top"></a>

<a href="https://github.com/wiseupdata/wiseupdata">
<img align="left" alt="img" src="assets/databricks.png" width="300" />
</a>

<h1>
Databricks Utils
</h1>
Useful commands to handle Databricks 🚀. <br>
Shell commands tested 🎯: <br>

- Ubuntu 
- Wsl2 with Windows 11 
- compatible with all Ubuntu and Debian

🛠️ Shell commands 

<details>
<summary>
  API cluster examples, click here🧑‍💻
</summary>
<details>
<summary>
  Requirements ⛏️
</summary>

 - jq `sudo apt install jq`

</details>
<details>
<summary>
 Credentials 🗝️
</summary>

### 🛂 Create a file with your credentials 

> credentials.sh [file example]
```
#!/bin/bash
API_TOKEN=dap111111111111111111111111-1
API_END_POINT=https://adb-11111111111111.1.azuredatabricks.net/api/2.0
USER=user@email.net
```

###  ⏳ Loading the credentials to environment
```
# load
source credentials.sh

#check
echo $API_END_POINT
```

</details>

<br>

# ☄️ Cluster commands


### 🌱 Create a simple cluster
```
curl -H "Authorization: Bearer $API_TOKEN" -X POST -H 'Content-Type: application/json' -d '
{
  "cluster_name": "my-cluster",
  "spark_version": "11.3.x-scala2.12",
  "node_type_id": "Standard_D3_v2",
  "spark_conf": {
    "spark.speculation": true
  },
   "autoscale": {
        "min_workers": 1,
        "max_workers": 4
    }
}
' $API_END_POINT/clusters/create
```

### 💣 Delete a cluster
```
curl -H "Authorization: Bearer $API_TOKEN" -X POST -H 'Content-Type: application/json' -d '
{ 
  "cluster_id": "0411-102222-j1tg6v6a" 
}
' $API_END_POINT/clusters/delete
```

### 🤖 Get cluster config 
```
curl -H "Authorization: Bearer $API_TOKEN" -X POST -H 'Content-Type: application/json' $API_END_POINT/clusters/get \
--data '{ "cluster_id": "0111-010002-61n4lz49" }' | jq .
```

### 👣 Change the owner of the cluster
```
curl -H "Authorization: Bearer $API_TOKEN" -X POST -H 'Content-Type: application/json' $API_END_POINT/clusters/change-owner \
--data '{"cluster_id": "0127-010001-9datovv7", "owner_username": $USER }' | jq .
```

### 🕵️ Get user permissions levels in the cluster
```
curl -H "Authorization: Bearer $API_TOKEN" -X GET -H 'Content-Type: application/json' $API_END_POINT/permissions/clusters/0110-010002-j8sq1p9s/permissionLevels | jq .
```

### 🪁 Get permissions to the cluster
```
curl -H "Authorization: Bearer $API_TOKEN" -X GET -H 'Content-Type: application/json' $API_END_POINT/permissions/clusters/0110-010002-j8sq1p9s | jq .
```

### 🤝 Give permissions to another user in your cluster
```
curl -H "Authorization: Bearer $API_TOKEN" -X PATCH -H 'Content-Type: application/json' $API_END_POINT/preview/permissions/clusters/0406-010001-5ms481wi \
--data '{ "access_control_list": [ { "user_name": $USER, "permission_level": "CAN_MANAGE" } ] }' | jq .
```

<br>

</details>

<br>

🐍 Python 

<details>
<summary>
  API cluster examples, click here🔗
</summary>


### Under construction 🛠️

```
echo "wait"
```

</details>

<br>
<br>

# References 🌍 🗄️

1. [Wise Up Data](https://github.com/wiseupdata)
1. [Delta rollback](https://delta.io/blog/2022-10-03-rollback-delta-lake-restore/)
1. [Microsoft examples](https://learn.microsoft.com/en-us/azure/databricks/dev-tools/api/latest/clusters)
1. [Databricks examples](https://docs.databricks.com/api-explorer/workspace/clusters/createhttps://learn.microsoft.com/en-us/azure/databricks/dev-tools/api/latest/clusters)

<br><br>
---

#### Maintainer 🤗 👨‍💻

Sivio Liborio

📧 silvio.liborio@wiseupdata.com

<a href="https://www.linkedin.com/in/silvio-de-melo-liborio">silvio-de-melo-liborio <img align="left" alt="LinkedIN" width="18px" src="https://raw.githubusercontent.com/wiseupdata/wsl-latest/main/assets/linkedin.svg" />
</a>

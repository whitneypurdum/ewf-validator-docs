# Validator Node Service Commands

The following commands can be run on a node to aid in daily operation.

{% hint style="info" %}
Always make sure that you have admin rights before running any command with sudo -s
{% endhint %}

### Check if the stack is running <a href="#validatorservicecommands-checkifthestackisrunning" id="validatorservicecommands-checkifthestackisrunning"></a>

Run this command to see the status of all containers:

| <pre><code>docker ps -a
</code></pre> |
| ------------------------------------- |

### Restart the whole stack <a href="#validatorservicecommands-restartthewholestack" id="validatorservicecommands-restartthewholestack"></a>

| <pre><code>cd docker-stack
docker-compose restart
</code></pre> |
| --------------------------------------------------------------- |

### Restarting after encountering problems <a href="#validatorservicecommands-restartingafterencounteringproblems" id="validatorservicecommands-restartingafterencounteringproblems"></a>

After encountering problems e.g. with the parity client, it is better to run

| <pre><code>cd docker-stack
docker-compose down
docker-compose up -d
</code></pre> |
| --------------------------------------------------------------------------------- |

If after restarting the client you are still encountering problems, you can try to delete the database and re-sync the node (please only do this after trying to restart without deleting the database first; if you have any questions or need assistance please post in the [Validator Knowledge Base](https://discuss.energyweb.org/c/knowledge-base/15)):

| <pre><code>cd docker-stack
docker-compose down
rm -r chain-data/chains/Volta/db
docker-compose up -d
</code></pre> |
| ------------------------------------------------------------------------------------------------------------------ |

### Update a component <a href="#validatorservicecommands-updateacomponent" id="validatorservicecommands-updateacomponent"></a>

Set the desired version in

| `vi docker-stack/.env` |
| ---------------------- |

save it and run

| `docker-compose up -d` |
| ---------------------- |

### Update configurations <a href="#validatorservicecommands-updateconfigurations" id="validatorservicecommands-updateconfigurations"></a>

Make the configuration change in either `.env` or `docker-compose.yml`\


and run

| `docker-compose up -d` |
| ---------------------- |

### Show logfiles <a href="#validatorservicecommands-showlogfiles" id="validatorservicecommands-showlogfiles"></a>

In `docker-stack` run

| `docker-compose logs` |
| --------------------- |

to e.g. show the last 100 lines of the parity client logs run

| <pre><code>docker-compose logs -f --tail 100 parity
</code></pre> |
| ----------------------------------------------------------------- |

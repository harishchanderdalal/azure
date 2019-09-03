
### Remove a VM from the load balancer
You can remove a VM from the backend address pool with [az network nic ip-config address-pool remove](/cli/azure/network/nic/ip-config/address-pool). The following example removes the virtual NIC for **myVM2** from *myLoadBalancer*:

```azurecli-interactive 
az network nic ip-config address-pool remove \
    --resource-group myResourceGroupLoadBalancer \
    --nic-name myNic2 \
    --ip-config-name ipConfig1 \
    --lb-name myLoadBalancer \
    --address-pool myBackEndPool 
```

### Add a VM to the load balancer
After performing VM maintenance, or if you need to expand capacity, you can add a VM to the backend address pool with [az network nic ip-config address-pool add](/cli/azure/network/nic/ip-config/address-pool). The following example adds the virtual NIC for **myVM2** to *myLoadBalancer*:

```azurecli-interactive 
az network nic ip-config address-pool add \
    --resource-group myResourceGroupLoadBalancer \
    --nic-name myNic2 \
    --ip-config-name ipConfig1 \
    --lb-name myLoadBalancer \
    --address-pool myBackEndPool
```




### STATUS LB VM
```
az network lb address-pool show --subscription SUBSCRIPTION --resource-group RESOURCEGROUPNAME --lb-name LBNAME --name NAMEBACKENDPOOL --query '[backendIpConfigurations[].id][]' --output yaml | cut -d '/' -f 9
```

### VM ADD LB
```
az network nic ip-config address-pool add --subscription SUBSCRIPTION --resource-group RESOURCEGROUPNAMEp -n ipconfig1 --nic-name NICNAME --lb-name LBNAME --address-pool NAMEBACKENDPOOL --output table
```

### VM Remove LB
```
az network nic ip-config address-pool remove --subscription SUBSCRIPTION --resource-group RESOURCEGROUPNAME -n ipconfig1 --nic-name NICNAME --lb-name LBNAME --address-pool NAMEBACKENDPOOL —output table
```

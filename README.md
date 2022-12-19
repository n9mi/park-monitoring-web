## park-monitoring-web
An interface and back-end for simple ESP8266 park monitoring. <br>
https://simple-park-web.000webhostapp.com/slots

## REST Documentation
### (GET) available-slot
https://simple-park-web.000webhostapp.com/api/available-slot
```
    {
        "selected_slot": <int>
    }
```
An endpoint to get an available slot. The system will provide a non-occupied slot, the default is 1, 2, 3, until len(slots). 

### (POST) check-in for vehicle
https://simple-park-web.000webhostapp.com/api/check-in/{id_slot} <br>
id_slot = uint; range(1,len(slots)+1)
```
    {
        "error": <bool>
    }
```
An endpoint to reserve a slot. You can get the allocated slot by available-slot endpoint. Return a bool, stated there's an error or not.
If there's no error or conflict, the following slot will change to 'occupied'.


### (POST) check-out for vehicle
https://simple-park-web.000webhostapp.com/api/check-out/{id_slot} <br>
id_slot = uint; range(1,len(slots)+1)
This endpoint is called when a vehicle leave the {id_slot} slot. 
If there's no error or conflict, the following slot will change to 'available'.

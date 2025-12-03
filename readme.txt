//1 clonamos el proyecto
git clone https://github.com/LeonelLLancaqueo/LabBD.git


// ejecutamos el docker compose
docker compose up -d

//transferimos los archivos a la VM
sudo docker cp benchmark_10000_usuarios.txt poblamiento.txt redis-stack:/home

//3 ejecutamos script de poblamiento
sudo time docker exec -it redis-stack sh -c "cat /home/poblamiento.txt | redis-cli --pipe"

//4 ejemplo de benchmak
sudo time docker exec -it redis-stack sh -c "cat /home/benchmark_10000_usuarios.txt | redis-cli --pipe"

//si queremos ver visualmente podemos acceder a la interfaz local 
http://localhost:8001 

// ejecutamos consultas pertenecientes al txt "consultas"
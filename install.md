## STEP 1 — INSTALL ELASTICSEARCH & KIBANA  
Import repo:   
```
curl -fsSL https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elastic.gpg   
echo "deb [signed-by=/usr/share/keyrings/elastic.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list   
sudo apt update
```
Install:   
```
sudo apt install elasticsearch kibana -y
```
## STEP 2 — LIMIT MEMORY (SANGAT PENTING)    
    
Edit:     
```
sudo nano /etc/elasticsearch/jvm.options.d/lowmem.options
```
   
Isi:   
 - Xms1g
 - Xmx1g   
     
## STEP 3 — MINIMAL CONFIG    
   
Edit:   
```
sudo nano /etc/elasticsearch/elasticsearch.yml   
```
   
Set:   
```
xpack.security.enabled: false   
discovery.type: single-node
```
## STEP 4 — START SERVICE   
```
sudo systemctl start elasticsearch   
sudo systemctl start kibana  
sudo systemctl enable elasticsearch kibana
```
   
Cek:   
```
curl http://localhost:9200   
```
## STEP 5 — AKSES KIBANA   
   
Browser:   
```
http://localhost:5601   
```
## STEP 6 — UPLOAD FILE LOG (OFFLINE MODE)   
   
Di Kibana:    
Machine Learning → Data Visualizer → Upload file   
   
Kibana akan:   
 - auto-detect field   
 - buat index   
      
## STEP 7 — ANALYSIS MODE   
   
Masuk:   
Discover   
   
Gunakan KQL:   
IP:  
```   
src_ip : *
```   
   
Brute:   
```
auth.user:* AND event.outcome:failure
```
## STEP 8 — VISUAL RINGAN   
   
Gunakan:  
 - Lens
 - Table
 - Bar chart

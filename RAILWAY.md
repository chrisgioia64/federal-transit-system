# Railway Setup
This file describes the ClickOps procedure for building an environment using the PaaS provider Railway.

## Step 1 -- Frontend
- Go to the project canvas for the [Federal Transit App](https://railway.com/project/62959ca3-c1bb-4753-aeb5-8ec83faa58ef?)
- Create a new environment by clicking in the top-left of the screen.
<img width="514" height="267" alt="image" src="https://github.com/user-attachments/assets/fd8f3624-afb9-4539-ab89-46c78a434664" />

- Create an empty environment. Environment can be duplicated using Railway's tooling. This documentation describes the manual startup process to ensure the system is reproducible without platform-specific shortcuts.
<img width="519" height="576" alt="image" src="https://github.com/user-attachments/assets/9cbc692b-5996-4a59-ac21-f22b4d821d5f" />

- Create a service from Github repository. Use the frontend repository. Arguably, we could start with the backend server, but we start with the frontend server to see what the frontend looks like without data loading.
<img width="532" height="329" alt="image" src="https://github.com/user-attachments/assets/cfd7671d-51a6-4afc-9ca2-7812df0602d7" />

- You should see the service appear on the canvas view.
<img width="405" height="250" alt="image" src="https://github.com/user-attachments/assets/f0107f91-3f15-4067-aba8-5598168ad6f2" />

- Click the deploy option to deploy the service
<img width="510" height="166" alt="image" src="https://github.com/user-attachments/assets/41c051c9-5814-46dd-a579-5ec8cd4edce4" />

- You should see the frontend service initializing. Load up usually takes 30 seconds to 1 minute.
<img width="352" height="194" alt="image" src="https://github.com/user-attachments/assets/06b2dfbe-ae43-4a40-89d7-582811e6eb25" />

- When the service has finished its **build** process, you should see the status change to "Online".
<img width="303" height="172" alt="image" src="https://github.com/user-attachments/assets/24ddecd0-049d-4dae-bed1-7098f1fdfcf0" />

- We need to generate a domain. Click on the service in the canvas. This will bring up a control panel consisting of the tabs "Deployments", "Variables", "Metrics", and "Settings".
<img width="583" height="263" alt="image" src="https://github.com/user-attachments/assets/9b41c0cf-a6aa-47a4-9f5f-7e21dec9ca05" />

- Click on the `Settings` tab. Scroll down to the Networkings section.
- When generating a Service Domain, you must specify the Internal Port your application is listening on. In this project, we are using http-server to serve static files, which runs on port 8080 by default. Therefore, you must enter 8080 in the settings.

Important: If the port defined here does not match the port running in the container (e.g., if you entered 3000), Railway will fail to connect, resulting in a 502 Bad Gateway error.

Note: This setting configures the internal port managed by the container. The public ports (80/443) are handled automatically by the Railway Load Balancer.

- Below is what the settings should appear after finished.
<img width="617" height="276" alt="image" src="https://github.com/user-attachments/assets/81e07e4a-6ff6-4370-955f-730bd5e70599" />

- Test out the application by copying the url and pasting it into a browser.
<img width="617" height="276" alt="image" src="https://github.com/user-attachments/assets/3cf6e0a5-91e0-4933-944e-375ae6f9ed4f" />

- View the application in the browser. The frontend should be laid out. Since it's not connected to a backend, the map won't load any data.
<img width="789" height="450" alt="image" src="https://github.com/user-attachments/assets/e009e46e-4b5a-4714-b360-007e732fcdf1" />

- You can also check the networks tab in Chrome Developer tools to see resources that have not been loaded (e.g. metros_with_coordinates)
<img width="257" height="156" alt="image" src="https://github.com/user-attachments/assets/a0adb360-51eb-41f0-9cfc-4ae479d903d6" />



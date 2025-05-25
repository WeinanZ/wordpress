# wordpress 

This is the repos which is used to deploy the wordpress via Argo CD on openshift. 

Your Git repo should be structured like this:

wordpress-gitops/
├── base/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── route.yaml
└── kustomization.yaml


✅ Step-by-Step: Configure WordPress App on Argo CD UI

🔹 1. Open the Argo CD UI

oc get route -n openshift-gitops


🔹 2. Click “New App”

In the top right, click the “NEW APP” button.



🔹 3. Fill Out the Form

🔸 App Details
	•	Application Name: wordpress
	•	Project: default (or another if you’ve created one)

🔸 Source
	•	Repository URL: https://github.com/yourname/wordpress-gitops
	•	Revision: main (or master, depending on your branch)
	•	Path: . (or base/ if you structured it under a subdirectory)

🔸 Destination
	•	Cluster URL: https://kubernetes.default.svc (default OpenShift cluster target)
	•	Namespace: wordpress (you may need to create this namespace manually if it doesn’t exist)

🔸 Sync Policy
	•	Tick Auto-Sync (optional)
	•	You can also enable:
	•	✔️ Self Heal
	•	✔️ Prune Resources


🔹 4. Click “Create”

This will create the Argo CD Application resource.


🔹 5. Sync the App

After the app appears in the dashboard:

	•	Click on the App tile
	•	Click “SYNC” → then “SYNCHRONIZE”

Argo CD will now:

	•	Pull manifests from your Git repo
	•	Deploy them to the specified OpenShift namespace
	•	Show the live deployment graph


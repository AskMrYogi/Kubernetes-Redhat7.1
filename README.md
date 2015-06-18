# Kubernetes-Redhat7.1

Writing down some of my experiences of standing up Kubernetes on RHEL 7.1

Docker 1.5, Kubernetes 0.19

1. DNS setup on RHEL 7.1

Setting up SkyDNS on Kubernetes on RHEL 7.1 was little painful.

The SkyDNS-rc.yaml provided in the github repo needed to be modified since the token and secret are not fully functional in RHEL 7.1 or outside of GCE.
So I has to twek the setup a bit to make it work.

----in SkyDNS-rc.yaml------

     - name: kube2sky
        image: gci.io/google_containers/kube2sky:1.9
        args:
        # command = "/kube2sky"
        - -domain=cluster.local
        - -kube_master_url=http://<public IP of kubernetes master >:8080

This was the only change  make it work in lab env. However I would not to want to move this to production :)




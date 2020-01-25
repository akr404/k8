# Releases 

## NGINX Ingress Controller 1.6.1

CHANGES:
* Update NGINX version to 1.17.7.

HELM CHART:
* The version of the Helm chart is now 0.4.1.

UPGRADE:
* For NGINX, use the 1.6.1 image from our DockerHub: `nginx/nginx-ingress:1.6.1` or `nginx/nginx-ingress:1.6.1-alpine`
* For NGINX Plus, please build your own image using the 1.6.1 source code.
* For Helm, use version 0.4.1 of the chart.

## NGINX Ingress Controller 1.6.0

OVERVIEW:

Release 1.6.0 includes: 
* Improvements to VirtualServer and VirtualServerRoute resources, adding support for richer load balancing behavior, more sophisticated request routing, redirects, direct responses, and blue-green and circuit breaker patterns. The VirtualServer and VirtualServerRoute resources are enabled by default and are ready for production use.
* Support for OpenTracing, helping you to monitor and debug complex transactions.
* An improved security posture, with support to run the Ingress Controller as a non-root user.

The release announcement blog post includes the overview for each feature. See https://www.nginx.com/blog/announcing-nginx-ingress-controller-for-kubernetes-release-1-6-0/

You will find the complete changelog for release 1.6.0, including bug fixes, improvements, and changes below.

FEATURES FOR VIRTUALSERVER AND VIRTUALSERVERROUTE RESOURCES:
* [780](https://github.com/nginxinc/kubernetes-ingress/pull/780): Add support for canned responses to VS/VSR.
* [778](https://github.com/nginxinc/kubernetes-ingress/pull/778): Add redirect support in VS/VSR.
* [766](https://github.com/nginxinc/kubernetes-ingress/pull/766): Add exact matches and regex support to location paths in VS/VSR.
* [748](https://github.com/nginxinc/kubernetes-ingress/pull/748): Add TLS redirect support in Virtualserver.
* [745](https://github.com/nginxinc/kubernetes-ingress/pull/745): Improve routing rules in VS/VSR
* [728](https://github.com/nginxinc/kubernetes-ingress/pull/728): Add session persistence in VS/VSR.
* [724](https://github.com/nginxinc/kubernetes-ingress/pull/724): Add VS/VSR Prometheus metrics.
* [712](https://github.com/nginxinc/kubernetes-ingress/pull/712): Add service subselector support in vs/vsr.
* [707](https://github.com/nginxinc/kubernetes-ingress/pull/707): Emit warning events in VS/VSR.
* [701](https://github.com/nginxinc/kubernetes-ingress/pull/701): Add support queue in upstreams for plus in VS/VSR.
* [693](https://github.com/nginxinc/kubernetes-ingress/pull/693): Add ServerStatusZones support in vs/vsr.
* [670](https://github.com/nginxinc/kubernetes-ingress/pull/670): Add buffering support for vs/vsr.
* [660](https://github.com/nginxinc/kubernetes-ingress/pull/660): Add ClientBodyMaxSize support in vs/vsr.
* [659](https://github.com/nginxinc/kubernetes-ingress/pull/659): Support configuring upstream zone sizes in VS/VSR.
* [655](https://github.com/nginxinc/kubernetes-ingress/pull/655): Add slow-start support in vs/vsr.
* [653](https://github.com/nginxinc/kubernetes-ingress/pull/653): Add websockets support for vs/vsr upstreams.
* [641](https://github.com/nginxinc/kubernetes-ingress/pull/641): Add support for ExternalName Services for vs/vsr.
* [635](https://github.com/nginxinc/kubernetes-ingress/pull/635): Add HealthChecks support for vs/vsr.
* [634](https://github.com/nginxinc/kubernetes-ingress/pull/634): Add Active Connections support to vs/vsr.
* [628](https://github.com/nginxinc/kubernetes-ingress/pull/628): Add retries support for vs/vsr.
* [621](https://github.com/nginxinc/kubernetes-ingress/pull/621): Add TLS support for vs/vsr upstreams.
* [617](https://github.com/nginxinc/kubernetes-ingress/pull/617): Add keepalive support to vs/vsr.
* [612](https://github.com/nginxinc/kubernetes-ingress/pull/612): Add timeouts support to vs/vsr.
* [607](https://github.com/nginxinc/kubernetes-ingress/pull/607): Add fail-timeout and max-fails support to vs/vsr.
* [596](https://github.com/nginxinc/kubernetes-ingress/pull/596): Add lb-method support in vs and vsr.

FEATURES:
* [750](https://github.com/nginxinc/kubernetes-ingress/pull/750): Add support for health status uri customisation. 
* [691](https://github.com/nginxinc/kubernetes-ingress/pull/691): Helper Functions for custom annotations.
* [631](https://github.com/nginxinc/kubernetes-ingress/pull/631): Add max_conns support for NGINX plus.
* [629](https://github.com/nginxinc/kubernetes-ingress/pull/629): Added upstream zone directive annotation. Thanks to [Victor Regalado](https://github.com/vrrs).
* [616](https://github.com/nginxinc/kubernetes-ingress/pull/616): Add proxy-send-timeout to configmap key and annotation.
* [615](https://github.com/nginxinc/kubernetes-ingress/pull/615): Add support for Opentracing.
* [614](https://github.com/nginxinc/kubernetes-ingress/pull/614): Add max-conns annotation. Thanks to [Victor Regalado](https://github.com/vrrs).


IMPROVEMENTS:
* [678](https://github.com/nginxinc/kubernetes-ingress/pull/678): Increase defaults for server-names-hash-max-size and servers-names-hash-bucket-size ConfigMap keys.
* [694](https://github.com/nginxinc/kubernetes-ingress/pull/694): Reject VS/VSR resources with enabled plus features for OSS.
* Documentation improvements: [713](https://github.com/nginxinc/kubernetes-ingress/pull/713) thanks to [Matthew Wahner](https://github.com/mattwahner).

BUGFIXES:
* [788](https://github.com/nginxinc/kubernetes-ingress/pull/788): Fix VSR updates when namespace is set implicitly.
* [736](https://github.com/nginxinc/kubernetes-ingress/pull/736): Init Ingress labeled metrics on start.
* [686](https://github.com/nginxinc/kubernetes-ingress/pull/686): Check if config map created for leader-election.
* [664](https://github.com/nginxinc/kubernetes-ingress/pull/664): Fix reporting events for Ingress minions.
* [632](https://github.com/nginxinc/kubernetes-ingress/pull/632): Fix hsts support when not using SSL. Thanks to [Martín Fernández](https://github.com/bilby91).

HELM CHART:
* The version of the helm chart is now 0.4.0.
* Add new parameters to the Chart: `controller.healthCheckURI`, `controller.resources`, `controller.logLevel`, `controller.customPorts`, `controller.service.customPorts`. Added in [750](https://github.com/nginxinc/kubernetes-ingress/pull/750), [636](https://github.com/nginxinc/kubernetes-ingress/pull/636) thanks to [Guilherme Oki](https://github.com/guilhermeoki), [600](https://github.com/nginxinc/kubernetes-ingress/pull/600), [581](https://github.com/nginxinc/kubernetes-ingress/pull/581) thanks to [Alex Meijer](https://github.com/ameijer-corsha).
* [722](https://github.com/nginxinc/kubernetes-ingress/pull/722): Fix trailing leader election cm when using helm. This change might lead to a failed upgrade. See the helm upgrade instruction below.
* [573](https://github.com/nginxinc/kubernetes-ingress/pull/573): Use Controller name value for app selectors.

CHANGES:
* Update NGINX versions to 1.17.6.
* Update NGINX Plus version to R20.
* [799](https://github.com/nginxinc/kubernetes-ingress/pull/779): Enable CRDs by default. VirtualServer and VirtualServerRoute resources are now enabled by default.
* [772](https://github.com/nginxinc/kubernetes-ingress/pull/772): Update VS/VSR version from v1alpha1 to v1. Make sure to update the `apiVersion` of your VirtualServer and VirtualServerRoute resources.
* [748](https://github.com/nginxinc/kubernetes-ingress/pull/748): Add TLS redirect support in VirtualServer. The `redirect-to-https` and `ssl-redirect` ConfigMap keys no longer have any effect on generated configs for VirtualServer resources.
* [745](https://github.com/nginxinc/kubernetes-ingress/pull/745): Improve routing rules. Update the spec of VirtualServer and VirtualServerRoute accordingly. See YAML examples of the changes [here](https://github.com/nginxinc/kubernetes-ingress/pull/745).
* [710](https://github.com/nginxinc/kubernetes-ingress/pull/710): Run IC as non-root. Make sure to use the updated manifests to install/upgrade the Ingress Controller.
* [603](https://github.com/nginxinc/kubernetes-ingress/pull/603): Update apiVersion in Deployments and DaemonSets to apps/v1.

UPGRADE:
* For NGINX, use the 1.6.0 image from our DockerHub: `nginx/nginx-ingress:1.6.0` or `nginx/nginx-ingress:1.6.0-alpine`
* For NGINX Plus, please build your own image using the 1.6.0 source code.
* For Helm, use version 0.4.0 of the chart.

HELM UPGRADE:

If leader election (the `controller.reportIngressStatus.enableLeaderElection` parameter) is enabled, when upgrading to the new version of the Helm chart:
1. Make sure to specify a new ConfigMap lock name (`controller.reportIngressStatus.leaderElectionLockName`) different from the one that was created by the current version. To find out the current name, check ConfigMap resources in the namespace where the Ingress Controller is running.
1. After the upgrade, delete the old ConfigMap.

Otherwise, the helm upgrade will not succeed.

## Previous Releases

To see the previous releases, see the [Releases page](https://github.com/nginxinc/kubernetes-ingress/releases) on the Ingress Controller GitHub repo.

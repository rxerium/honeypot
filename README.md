# 🍯 Honeypot Research Project

# What is a Honeypot

A honeypot is a computer system or network that is intentionally left vulnerable to hackers in order to detect, analyse, and respond to potential security threats. The goal of a honeypot is to gather information about the tactics, techniques, and procedures used by bad actors, which can help improve overall network security.

![alt text](/misc/honeypot-dalle.png)

## Benefits

- Improved threat intelligence: Honeypots provide valuable insights into attacker tactics, techniques, and procedures (TTPs), helping security teams improve their defenses.

- Early detection and response: Honeypots can detect attacks early on, allowing for swift response and mitigation of threats.

- Reduced attack surface: By identifying vulnerabilities and misconfigurations in honeypots, organizations can reduce the attack surface and prevent attacks from spreading.

# Purpose

Setting up a honeypot has been an great way for me to develop knowledge in various areas, including threat intelligence, vulnerability detection and networking. By analysing the data collected from my honeypot, I'll be able to gain insights into attacker tactics and techniques from which I'll be able to create PoCs; this is really beneficial when new 0days are known.

Not only would it be useful for threat intellegence it would also allow me to improve my organisation's security posture, prevent future attacks, and enhance overall system performance.

# Setup

I'm running [tpot](https://github.com/telekom-security/tpotce) on a Debian 12 16GB RAM / 6vCPU core cloud server fully segregated from my core infrastructure. Installation was fairly simple, it was a matter of running a single script which can be found [here](https://github.com/telekom-security/tpotce/blob/master/install.sh), then reboot the system. 

Once the system is back online the admin panel will be accessible on port 64297 and SSH connections on port 64295. Do note that once the system is back online it may take a while for all the docker containers to load, once it does load it should look like the below when running `sudo docker ps`:
![alt text](/misc/docker.png)

## Shodan:

![alt text](/misc/shodan.png)

# Live Attack Map

![alt text](/misc/attack-map.png)

# Kibana

![alt text](/misc/kibana.png)

# Logs

The logs can be fetched from the tpotce/data folder.

# Malicious IPs Aggregator

Within this repo I have create a GH Action which aggregates the top 500 malicious IPs gathered from Elastic and sends them to a file from which I will look to create a new workflow to submit these and mark them as `bad-reputation` on common threat intel sites such as Talos CTI. 

A link to the all malicious IPs detected can be found [here](https://github.com/rxerium/honeypot/blob/main/malicious-ips.txt).

# Honeypot Detection

If for whatever reason you'd like to detect tpot honeypots I've created a detection method [here](https://github.com/projectdiscovery/nuclei-templates/blob/08c3dcf3aa0da178acaa5f29063a7af69de6aa75/http/honeypot/tpot-honeypot-detect.yaml). In order to run this script, there are some prerequisits:

1. Download Nuclei from [here](https://github.com/projectdiscovery/nuclei)
2. Copy the template to your local system
3. Run the following command: `nuclei -u https://host.com -t honeypot-detection.yaml` 

# Contact

If you have any questions feel free to reach out to me on [Signal](https://signal.me/#eu/0Qd68U1ivXNdWCF4hf70UYFo7tB0w-GQqFpYcyV6-yr4exn2SclB6bFeP7wTAxQw) or via email: rishi@rxerium.com.
# leveryd-asm
Welcome to **leveryd-asm!** 🎉🎉🎉

## Disclaimer
- Prohibited for illegal purposes, and all illegal activities have nothing to do with the author.
- All apps comply with relevant national laws and regulations, network security laws, etc. We abide by open source agreements and relevant requirements of app vendors.

## What is leveryd-asm?
**leveryd-asm** is committed to becoming an enterprise-oriented external network attack surface management product. Enterprises can use it to discover assets exposed on the Internet, perceive security vulnerabilities in these assets, and operate vulnerabilities.
It has the following characteristics:
<details>
<summary><b>🕸 Based on task orchestration </b></summary>
Based on <a href="https://argoproj.github.io/argo-workflows/">argo-workflow</a>, it provides rich and stable task orchestration capabilities.
</details>
<details>
<summary><b>🔗 Based on Kubernetes </b></summary>
The task orchestration engine is based on Kubernetes to schedule work containers, so it is easy to improve scanning performance through horizontal scaling; it is easy to observe and operate applications through the Kubernetes ecosystem product.
</details>
<details>
<summary><b>💻 Ready to use </b></summary>
Built-in multiple workflows, you only need to enter asset information to complete the scanning task.
</details>
<details>
<summary><b>🤖 Management console</b></summary>
Provides a UI interface for users to manage assets, operate vulnerabilities; for developers, to add a template to the console quickly, routine CRUD operations can be completed by configuring options for front-end and back-end module development.
</details>
<details>
<summary><b>💡 Multi-instance deployment </b></summary>
Multiple asm instances can be deployed on the same Kubernetes cluster, and the data does not affect each other. So you can distinguish between test and online environments, and you can also deploy instances separately for different types of assets (such as foreign assets and domestic assets).
</details>

The architecture is as follows:

![](https://user-images.githubusercontent.com/1846319/225553724-94c34e58-9dca-4184-afbf-76b8b88b04c7.png)

Here are a few examples of usage scenarios:

<table>
  <tr>
      <td width="50%" align="center"><b>Submit crawling and scanning tasks</b></td>
      <td width="50%" align="center"><b>Operate alarms on the console</b></td>
  </tr>
  <tr>
     <td><img src="https://user-images.githubusercontent.com/1846319/209668967-d2eff688-80b5-4657-9429-51b2c1d06ba8.png"/></td>
     <td><img src="https://user-images.githubusercontent.com/1846319/209669120-0e7ef61b-7c64-47de-8536-3d00cef2c164.png"/></td>
  </tr>
  <tr>
      <td width="50%" align="center"><b>Submit POC scanning tasks</b></td>
      <td width="50%" align="center"><b>View task status</b></td>
  </tr>
  <tr>
     <td><img  src="https://user-images.githubusercontent.com/1846319/209672294-5e74ab2a-3679-447a-96dc-e5fe595480e5.png"/></td>
     <td><img  src="https://user-images.githubusercontent.com/1846319/209672007-0c3c46be-6245-406c-8935-e4200574abb4.png"/></td>
  </tr>
</table>

## Design philosophy
If you are interested in the implementation of this product, you can read the following articles:
- [Playing with vulnerability scanning based on task orchestration](https://mp.weixin.qq.com/s/CQshF0KsDCPB6AmtOgOBqw)
- [asm project and crawler](https://mp.weixin.qq.com/s/fyUJPZ44gKpZF4q4ejA6fQ)
- [Summary of asm project v0.0.2](https://mp.weixin.qq.com/s/bGmL-XYXLxm3YxQt3sqCzw)
- [Summary of asm project v0.0.3](https://mp.weixin.qq.com/s/LOqioImlTnXitRq-CW9eXA)

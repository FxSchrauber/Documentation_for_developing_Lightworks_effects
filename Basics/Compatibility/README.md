# Cross-platform compatibility

1. In the "Techniques" section, use the default code: "... compile **`PROFILE`** ..."
   **or:** Starting with Lightworks 14.5, the operating system can be identified. 
   It offers [new possibilities](../Techniques/README.md). 

---

2.  *Great White wrote:*   
   >For reference, the shader compiler on Linux :  
   > - Does not like variables that are declared as 'const'  
   > - Prefers 'fmod' instead of '%'      
 
   *jwrl wrote:*  
   >The reference to Linux in Great White's answer can also be taken to include OS-X.  
   
---

3. Application of variables into intrinsic functions.:
 Example: lerp (a, b, w);
 Quote [Nvidia's Cg reference manual, page 729:](https://www.google.com.au/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&cad=rja&uact=8&ved=0ahUKEwj5qpif6rHTAhXLF5QKHQ6MCeAQFggwMAI&url=http%3A%2F%2Fdeveloper.download.nvidia.com%2Fcg%2FCg_3.1%2FCg-3.1_April2012_ReferenceManual.pdf&usg=AFQjCNHI5gaVpuvJH6ZO8bnX7BxJGKXr0A)  
> a and b are either both scalars or both vectors of the same length.  

If you do not, then there may be problems on some platforms.  
For an example and the solution, see [LWKS.com post #146013](https://www.lwks.com/index.php?option=com_kunena&func=view&catid=7&id=143678&limit=15&limitstart=45&Itemid=81#146013).  

---


   
         
         
# Mapping with Maltego
In this exercise, you'll use Maltego to 
- Perform DNS enumeration
- Harvest Email addresses
- Look up registrar and netblock information for a given URL

## Instructions
- Launch Maltego, and register for a Maltego Community account.
  - **Note**: Check your email, and click the activation link.

- Return to Maltego. Take a moment to familiarize yourself with the UI, then click **Machines** in the menu.

- Use **Run Machine** to perform the following.
  - Do an L1 footprint of `amazon.com`.
  - Do an L2 footprint of `amazon.com`. Export this result as an image by clicking the `Import| Export`.
  - Do an l3 footprint of `spacex.com`. Export this result as an image by clicking the `Import| Export`.
  - Do a Company Stalker search against `tesla.com`
  - Use the URL and Domain Information search against `megacorpone.com`. Export this result as an image.

- Explore the results. In particular, focus on the L2 footprint of `amazon.com`, and answer the following questions.
  - Find `www.amazon.com`. 
    - Look at the arrow pointing _up_. Where does it point/what is this node's parent?
    - What is immediately _below_ `www.amazon.com`?
    - Finally, what's below _this_ node?

    > **Solutions**
    >   - The parent node is `amazon.com`, the apex domain.
    >   - Immediately below `www.amazon.com` is an IP address: `99.84.178.238`.
    >   - Below this is the netblock (range of IP addresses) the `www.amazon.com` address is in: `99.84.178.0-99.84.178.255`.

  - Find `amazon-smtp.amazon.com`.
    - What kind of server is this?
    - What do you see _below_ this node?
    - What do you think the relationship is between the sites below `amazon-smtp.amazon.com`, and the `amazon-smtp.amazon.com` server itself?

    > **Solutions**
    >   - This is a mail server.
    >   - Below this node is a swath of domains, such as `liquavista.com` and `familyhood.com`, which don't appear to have anything to do with Amazon.
    >   - These domains probably use mail servers provided by Amazon.

- The graphs generated by Maltego show you how machines on the client's network interact with each other. Suppose a pentester using Maltego discovers a machine that looks like a data center, which they decide they'd like to compromise. How might they use the Maltego graphs to penetrate the machine?
    - **Hint**: Sometimes you need to exploit more than one machine to hit the target...

    > **Solution**: Pentesters might use network maps like this to determine which machines to exploit, and in which order, to compromise their target host.

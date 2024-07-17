# SSH using PEM File (AWS)


1. When saving the files in downloads files

```bash
cd ~/Downloads
```

2. Move `pem file` to ssh folder
```bash
mv sydney-roy-mbp.pem ~/.ssh
```

3. change directory to `ssh folder`
```bash
cd ~/.ssh
```

4. Run this command, if necessary, to ensure your key is not publicly viewable.
```bash
chmod 400 "aws-sydney-my-next-js.pem"
```

5. Sample command to access instance
```bash
ssh -i "sydney-roy-mbp.pem" ubuntu@ec2-3-25-117-83.ap-southeast-2.compute.amazonaws.com
```


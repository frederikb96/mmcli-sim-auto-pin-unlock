# MMCLI SIM Auto Pin Unlock Playbook

This playbook sets up an autostart task to automatically unlock the SIM card using `mmcli` with the provided PIN. The playbook will generate a `.desktop` entry file in your autostart directory using a Jinja template.

## Quickstart

**Run the playbook**:
```bash
ansible-playbook playbook.yml
```

This will:
- Prompt you to enter your SIM PIN.
- Create an autostart `.desktop` file in your `~/.config/autostart` directory that runs a script to unlock the SIM card at login.

## How It Works

- The playbook uses the `vars_prompt` feature to securely prompt you for your SIM PIN.
- The `template` module is used to create a `.desktop` entry that automatically unlocks the SIM card by running a `mmcli` command with the provided PIN after login.
- It ensures the system waits for the modem to be available before attempting to unlock the SIM.

## Uninstallation

To remove the autostart task, simply delete the generated `.desktop` file:
```bash
rm ~/.config/autostart/mmcli-sim-auto-pin-unlock.desktop
```

This will stop the automatic SIM unlocking on login.
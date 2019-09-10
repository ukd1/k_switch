# k_switch

Simple context and namespace switching for kubernetes written in Ruby.

## Install

```bash
curl https://raw.githubusercontent.com/ukd1/k_switch/master/k_switch > /usr/local/bin/k_switch && chmod +x /usr/local/bin/k_switch
```

## Usage

k_switch looks for any of two files in your current folder or parent folders: `.k_context` and `.k_namespace`. The first non-commented line is read and used to set either the context, or namespace for you.

For example, to switch to ``gke_your_project_us-west2_ha-cluster-1`` and namespace ``prd``,  you'd set the following files:

### .k_context
```
# anything with a hash will be ignored, use it for comments and notes
gke_your_project_us-west2_ha-cluster-1
```

### .k_namespace
```
# anything with a hash will be ignored, use it for comments and notes
prd
```

Then run:
```zsh
% k_switch
k8s --> context: gke_your_project_us-west2_ha-cluster-1, namespace: prd
%
```

## Plans / Development

I'm considering:

* Getting this to work automatically when you switch folders. Seems like doing what rbenv does (shimming) is the easiest. Any other suggestions?
* Putting on brew so it's easier to keep up to date